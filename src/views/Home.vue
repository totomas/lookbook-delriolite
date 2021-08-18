<template>
  <div>
    <div class="lookbook-container">
      <div class="loading" v-if="isLoading">
        <img src="../assets/img/logo-comuna.png" />
        <progress-bar
          class="loadingBar"
          bar-color="#fff"
          bg-color="#e40524"
          text-fg-color="#fff"
          size="medium"
          :val="increasing_pct"
          :text="increasing_pct + '%'"
        />
      </div>
      <div class="instructions" v-show="isCover">
        <p>Para una mejor experiencia, navega con los botones</p>
        <div class="instructions_page-btn">
          <img src="../assets/img/up-arrow.png" alt="" />
          <img src="../assets/img/arrow-down.png" alt="" />
        </div>
        <button class="instructions_btn" @click="isCover = !isCover">
          Empezar a navegar
        </button>
      </div>
      <div class="verlite" v-show="verLite">
        <span @click="verLite = !verLite">X</span>
        <p>Para una experiencia única ve la versión Full</p>
        <a href="https://bricsa.cl/wp-content/lookbook/delrio.html">Ver Full</a>
      </div>
      <div class="page-btn">
        <a
          :href="'#section0' + currentStep"
          @click="Prev"
          :class="[currentStep == '1' ? 'disabled' : '']"
        >
          <img src="../assets/img/up-arrow.png" alt=""
        /></a>
        <a
          :href="'#section0' + currentStep"
          @click="Next"
          :class="[currentStep == '14' ? 'disabled' : '']"
        >
          <img src="../assets/img/arrow-down.png" alt=""
        /></a>
      </div>
      <progress-bar
        class="bar-progress"
        bar-color="#e40524"
        bg-color="#fff"
        :val="currentStep * 7.2"
      />
      <span class="bricsa-square"></span>
      <div class="section section01-container" id="section01">
        <div class="section-01">
          <div class="section-bg01">
            <div id="section-bg01" :class="{ enter: !isCover }" />
          </div>
          <img
            lazyload
            class="section-logo"
            src="../assets/img/logo-comuna.png"
          />
          <div id="section-01__text">
            <p class="call">City Lovers</p>
            <p class="downgrade">
              Vive conectado a la energía urbana de Santiago
            </p>
          </div>
          <div class="uptext">
            <p v-scrollanimation id="section1_citylover">City Lovers</p>
          </div>
        </div>
      </div>
      <div class="section section02-container" id="section02">
        <img src="../assets/img/02.jpg" />
        <div class="section-02" id="section-02">
          <img src="../assets/img/02-2.png" alt="" />
          <p class="title">Un edificio que</p>
          <p class="subtitle">marca tendencia</p>
          <p class="downgrade">Arquitectura integrada a la ciudad.</p>
        </div>
      </div>
      <div class="section section03-container" id="section03">
        <video
          muted
          playsinline
          autoplay
          loop
          preload="auto"
          class="section-bg"
        >
          <source src="../assets/img/video01.mp4" type="video/mp4" />
        </video>
        <div class="section-03">
          <p v-scrollanimation class="title" id="section-03_title">
            La naturaleza también vive en la ciudad
          </p>
          <div class="section03-content">
            <div v-scrollanimation class="section-03_02" id="section-03_02">
              <p class="title02">Jardineras colgantes</p>
              <p class="subtitle">
                La naturaleza siempre es una gran compañera.
              </p>
            </div>
          </div>
          <div class="section03-content_img">
            <img
              v-scrollanimation
              src="../assets/img/08.jpg"
              class="section-03_02-img"
              id="section-03_02-img"
            />
          </div>
        </div>
      </div>
      <div class="section section04-container" id="section04">
        <div class="section-04">
          <img
            v-scrollanimation
            src="../assets/img/06.jpg"
            class="section04_img"
            id="section04_img"
          />
        </div>
      </div>
      <div class="section section05-container" id="section05">
        <div class="section-05">
          <div class="section05_video">
            <video
              muted
              playsinline
              autoplay
              loop
              preload="auto"
              class="section-bg"
              id="section05_video"
            >
              <source src="../assets/img/video02.mp4" type="video/mp4" />
            </video>
            <p v-scrollanimation id="section05_video-text" class="title">
              ¿Hagamos un picnic?
            </p>
          </div>
          <div class="section05_img">
            <img src="../assets/img/12.jpg" id="section05_img" />
            <p v-scrollanimation id="section05_img-text" class="subtitle">
              Rodeado de plazas y áreas verdes
            </p>
          </div>
        </div>
      </div>
      <div class="section section06-container" id="section06">
        <div class="section-06">
          <video
            muted
            playsinline
            autoplay
            loop
            preload="auto"
            class="section-bg"
            id="section06_video"
          >
            <source src="../assets/img/video03.mp4" type="video/mp4" />
          </video>
          <div v-scrollanimation id="section06_text">
            <p class="title">Conectado con</p>
            <p class="subtitle">una gran ciclovía</p>
          </div>
        </div>
      </div>
      <div class="section section07-container" id="section07">
        <video
          muted
          playsinline
          autoplay
          loop
          preload="auto"
          class="section-bg"
          id="section07_video"
        >
          <source src="../assets/img/video04.mp4" type="video/mp4" />
        </video>
        <div class="section-07">
          <div class="section07_text">
            <p class="title">54</p>
            <p class="subtitle">
              <strong>bicicleteros con taller</strong><br />en acceso al
              edificio
            </p>
          </div>
          <p v-scrollanimation class="downgrade" id="section07_downgrade">
            Una ciudad que se pedalea es una mejor ciudad
          </p>
        </div>
      </div>
      <div class="section section08-container" id="section08">
        <video
          muted
          playsinline
          autoplay
          loop
          preload="auto"
          class="section-bg"
          id="section08_video"
        >
          <source src="../assets/img/video05.mp4" type="video/mp4" />
        </video>
        <div class="section-08">
          <img src="../assets/img/14.jpg" />
          <p class="title">¿Un cafecito?</p>
          <p class="subtitle">
            El corazón de <br />
            Providencia <br />
            está lleno de ellos.
          </p>
        </div>
      </div>
      <div class="section section09-container" id="section09">
        <video
          muted
          playsinline
          autoplay
          loop
          preload="auto"
          class="section-bg"
          id="section09_video"
        >
          <source src="../assets/img/video06.mp4" type="video/mp4" />
        </video>
        <div class="section-09">
          <p class="title">¡Voy y vuelvo!</p>
          <p class="subtitle">
            Cercano a cafeterías, almacenes de barrios y servicios.
          </p>
        </div>
      </div>
      <div class="section section10-container" id="section010">
        <div class="section10-img">
          <img
            v-scrollanimation
            class="section-bg"
            id="section10_bg"
            src="../assets/img/05.jpg"
          />
        </div>
        <div class="section10-text">
          <div v-scrollanimation class="section-10" id="section10-content">
            <img src="../assets/img/11.jpg" />
            <p class="title">La ciudad también se merece un descanso</p>
          </div>
        </div>
      </div>
      <div class="section section11-container" id="section011">
        <img
          v-scrollanimation
          class="section-bg"
          id="section11_bg"
          src="../assets/img/15.jpg"
        />
        <div class="section-11" id="section11-content">
          <p class="title">Un City lover pone ojo en...</p>
          <p class="subtitle">los detalles</p>
          <p class="downgrade">Terminaciones de 1er nivel.</p>
        </div>
      </div>
      <div class="section section12-container" id="section012">
        <img
          v-scrollanimation
          class="section-bg"
          id="section12_bg"
          src="../assets/img/04.jpg"
        />
        <div class="section12-text">
          <div v-scrollanimation class="section-12" id="section12_content">
            <p class="title">Nada como</p>
            <p class="subtitle">una buena ducha</p>
            <p class="downgrade">Cómodo baño principal con shower door.</p>
          </div>
        </div>
      </div>
      <div class="section section13-container" id="section013">
        <img class="section-bg" id="section13_bg" src="../assets/img/08.jpg" />
        <img id="section13_img" src="../assets/img/10.jpg" />
        <div id="section13_content" class="section-13">
          <p class="title">Lleva la entretención a lo más alto</p>
          <p class="subtitle">Departamentos con terraza privada en rooftop.</p>
        </div>
      </div>
      <div class="section section14-container" id="section014">
        <img class="section-bg" id="section14_bg" src="../assets/img/13.jpg" />
        <img id="section14_img" src="../assets/img/03.jpg" />
        <p class="title" id="section14_title">Áreas comunes</p>
        <div id="section14_content" class="section-14">
          <p class="subtitle">Un City lover</p>
          <p class="downgrade">sabe pasarlo bien</p>
        </div>
      </div>
      <div class="section section15-container" id="section015">
        <video
          muted
          playsinline
          autoplay
          loop
          preload="auto"
          class="section-bg"
          id="section15_video"
        >
          <source src="../assets/img/video07.mp4" type="video/mp4" />
        </video>
        <div class="section15_img01"></div>
        <div class="section15_img02"></div>
        <div class="section-15">
          <img src="../assets/img/07.jpg" />
          <p class="title">Cuando la temperatura sube:</p>
          <p class="subtitle" id="section15_subtitle">¡baja y refréscate!</p>
          <p class="downgrade" id="section15_downgrade">
            Piscina, Quincho y Salón Gourmet.
          </p>
        </div>
      </div>
      <div class="section section16-container" id="section016">
        <video
          muted
          playsinline
          autoplay
          loop
          preload="auto"
          class="section-bg"
          id="section16_video"
        >
          <source src="../assets/img/video08.mp4" type="video/mp4" />
        </video>
        <div class="section-16">
          <p class="title">¿eres?</p>
          <p class="subtitle">#Citylover</p>
          <img lazyload src="../assets/img/logo-comuna.png" />
        </div>
      </div>
      <div class="section section17-container" id="section017">
        <div class="section-17">
          <img lazyload class="logo" src="../assets/img/bricsa.png" />

          <img lazyload class="bptl" src="../assets/img/bptl.png" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ProgressBar from "vue-simple-progress";
export default {
  components: {
    ProgressBar,
  },
  data() {
    return {
      currentStep: "1",
      isLoading: true,
      increasing_pct: 0,
      isCover: true,
      verLite: true,
    };
  },
  methods: {
    load() {
      this.isLoading = true;
      setTimeout(() => {
        this.isLoading = false;
      }, 5000);
    },
    Prev() {
      this.currentStep--;
    },
    Next() {
      this.currentStep++;
    },
  },
  created() {
    this.load();
    setInterval(() => {
      if (this.is_paused) return;

      this.increasing_pct = Math.min(this.increasing_pct + 1, 100);
    }, 23);
  },
};
</script>

<style lang="scss" scoped>
.lookbook-container {
  position: relative;
  overflow: hidden;
  height: 100vh;
}
.section {
  position: relative;
  overflow: hidden;
  min-height: 101vh;
}

.bricsa-square {
  display: block;
  position: fixed;
  right: 0;
  top: 20px;
  width: 50px;
  height: 50px;
  background: #e40524;
  z-index: 99;
}
@keyframes breath {
  0% {
    transform: scale(0.9);
  }
  100% {
    transform: scale(1);
  }
}
.loading {
  transition: all 1s both;
  background: #e40524;
  z-index: 100;
  position: absolute;
  display: grid;
  grid-template-rows: repeat(2, min-content);
  row-gap: 20px;
  justify-content: center;
  justify-items: center;
  align-items: center;
  align-content: center;
  width: 100%;
  height: 100vh;
  img {
    animation: breath 1s both infinite alternate-reverse;
    width: 40%;
  }
  .loadingBar {
    width: 60%;
  }
}

.instructions {
  background: #e40524;
  position: relative;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  display: grid;
  justify-content: center;
  justify-items: center;
  align-content: center;
  align-items: center;
  row-gap: 30px;
  z-index: 14;
  p {
    color: #fff;
    font-size: 26px;
    width: 90%;
    text-align: center;
    font-weight: 300;
    margin: 0;
  }
  .instructions_page-btn {
    width: 50px;
    display: grid;
    justify-items: center;
    align-items: center;
    position: relative;
    border: solid 1px #fff;
    img {
      width: 70%;
      padding: 5px;
      border: none;
      background: #e40524;
    }
  }
  .instructions_btn {
    color: #fff;
    background: rgba(0, 0, 0, 0);
    border: solid 2px #fff;
    border-radius: 10px;
    padding: 10px;
    cursor: pointer;
    transition: 400ms;
    &:hover {
      background: #b9041c;
    }
  }
}
@keyframes arrow-down {
  0% {
    margin-top: 0;
  }
  100% {
    margin-top: 10px;
  }
}

.verlite {
  background: #e40524;
  color: #fff;
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 100px;
  display: grid;
  grid-template-rows: min-content;
  justify-content: center;
  justify-items: center;
  align-content: center;
  align-items: center;
  row-gap: 10px;
  z-index: 14;

  span {
    cursor: pointer;
    position: absolute;
    top: 5px;
    right: 10px;
  }
  p {
    margin: 0;
  }

  a {
    color: #fff;
    background: rgba(0, 0, 0, 0);
    border: solid 2px #fff;
    border-radius: 10px;
    padding: 5px 10px;
    cursor: pointer;
    transition: 400ms;
    text-decoration: none;

    &:hover {
      background: #b9041c;
    }
  }
}

.page-btn {
  z-index: 13;
  position: fixed;
  bottom: 0;
  right: 0;
  display: grid;
  a {
    width: 30px;
    height: 30px;
    padding: 10px;
    border: none;
    background: #e40524;
    cursor: pointer;
    transition: 400ms;
    &:hover {
      background: #b9041c;
    }
    img {
      width: 100%;
    }
  }
  .disabled {
    pointer-events: none;
  }
}

.bar-progress {
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 13;
}

.section-bg {
  height: 100%;
  object-fit: cover;
  position: absolute;
  z-index: -1;
  left: -100%;
}
.section01-container {
  .section-bg01 {
    #section-bg01 {
      transition: all ease-in-out;
      transition-duration: 4s;
      width: 100%;
      height: 100vh;
      background: url("../assets/img/01.jpg") no-repeat;
      background-position-x: -100px;
      filter: brightness(0.8);
    }
    .enter {
      background-position-x: -630px !important;
    }
  }
  .section-01 {
    background: rgba(0, 0, 0, 0.3);
    width: 100%;
    height: 100%;
    position: absolute;
    display: block;
    top: 0;
    left: 0;
    z-index: 1;
    .section-logo {
      width: 100px;
      position: absolute;
      top: 50px;
      left: 20px;
    }
    .call {
      transition: all 400ms;
      text-align: left;
      color: #fff;
      font-size: 54px;
      font-weight: bolder;
      line-height: 0.8;
      margin: 0;
    }
    .downgrade {
      text-align: left;
      color: #fff;
      font-size: 29px;
      font-weight: 300;
      line-height: 1;
      margin: 0;
    }
    .uptext {
      #section1_citylover {
        transition: all ease-in-out;
        transition-duration: 4s;
        transform: rotate(-90deg) scale(2.2);
        font-size: 120px;
        position: absolute;
        right: -230px;
        margin: 0;
        font-weight: bolder;
        color: #e40524;
        bottom: -99%;
        z-index: 1;
        white-space: nowrap;
      }
      .enter {
        bottom: 100% !important;
      }
    }
    #section-01__text {
      width: 70%;
      display: grid;
      row-gap: 20px;
      position: absolute;
      top: 28%;
      left: 20px;
      z-index: 2;
    }
  }
}
.section02-container {
  position: relative;
  img {
    width: 100%;
    height: 100%;
    left: 0;
    position: absolute;
    object-fit: cover;
  }
  .section-02 {
    position: absolute;
    width: 80%;
    height: 60%;
    left: 10%;
    top: 20%;
    display: grid;
    justify-content: center;
    justify-items: center;
    align-items: center;
    align-content: center;
    grid-template-rows: repeat(3, min-content);
    row-gap: 20px;
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      filter: brightness(0.7);
      z-index: 0;
    }
    .title {
      color: #fff;
      width: 100%;
      font-size: 40px;
      text-align: center;
      top: 20%;
      font-weight: 300;
      line-height: 0.9;
      z-index: 1;
      margin: 0;
    }
    .subtitle {
      color: #fff;
      width: 100%;
      font-weight: 800;
      font-size: 50px;
      text-align: center;
      top: 30%;
      line-height: 1;
      z-index: 1;
      margin: 0;
    }
    .downgrade {
      color: #fff;
      width: 80%;
      font-weight: 300;
      font-size: 30px;
      text-align: center;
      top: 70%;
      left: 10%;
      line-height: 1;
      z-index: 1;
      margin: 0;
    }
  }
}
.section-03 {
  position: relative;
}
.section03-container {
  .section-bg {
    position: absolute;
    z-index: 3;
    width: 100%;
    height: 100vh;
    top: 0;
    left: 0;
  }
  .section-03 {
    background: rgba(0, 0, 0, 0.3);
    width: 100%;
    height: 100%;
    position: absolute;
    display: block;
    top: 0;
    left: 0;
    z-index: 3;
    display: grid;
    align-items: center;
    justify-content: center;
    .title {
      transition: all 4s 2s;
      display: flex;
      justify-content: center;
      align-items: center;
      position: absolute;
      color: #fff;
      width: 80%;
      height: 40%;
      font-size: 60px;
      text-align: center;
      top: 30%;
      left: 10%;
      font-weight: 800;
      line-height: 0.9;
      z-index: 3;
      margin: 0;
    }
    .enter {
      top: -100%;
    }
    .section03-content {
      .section-03_02 {
        transition: all 2s 4s ease-in-out;
        position: absolute;
        top: 98%;
        left: 10%;
        width: 80%;
        height: 40%;
        display: grid;
        justify-items: center;
        align-items: center;
        row-gap: 20px;
        grid-template-rows: repeat(2, min-content);
        z-index: 2;
        .title02 {
          font-size: 56px;
          color: #fff;
          font-weight: 800;
          text-align: center;
          line-height: 1;
          margin: 0;
        }
        .subtitle {
          font-size: 26px;
          font-weight: 300;
          text-align: center;
          color: #fff;
          margin: 0;
        }
      }
      .enter {
        top: 30% !important;
        opacity: 1;
      }
    }
    .section03-content_img {
      .section-03_02-img {
        transition: all 2s 4s ease-in-out;
        position: absolute;
        height: 80%;
        width: 70%;
        top: 10%;
        left: -69%;
        object-fit: cover;
        object-position: 90% 0;
        filter: brightness(0.7);
        z-index: 1;
      }
      .enter {
        left: 0;
      }
    }
  }
}
.section04-container {
  .section-04 {
    img {
      transition: all 6s ease-in-out;
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      object-position: 0 0;
      filter: brightness(0.8);
    }
    .enter {
      object-position: 100%;
    }
  }
}
.section05-container {
  .section-bg {
    height: 70%;
    width: 100%;
    object-fit: cover;
    position: absolute;
    z-index: -1;
    left: 0;
    filter: brightness(0.6);
  }
  .section-05 {
    background: rgba(0, 0, 0, 0.3);
    width: 100%;
    height: 100%;
    position: absolute;
    display: block;
    top: 0;
    left: 0;
    z-index: 1;
    .section05_video {
      width: 100%;
      height: 70%;
      position: relative;
      #section05_video-text {
        transition: all 2s;
        position: absolute;
        bottom: -50%;
        left: 5%;
        color: #fff;
        width: 90%;
        font-size: 60px;
        text-align: center;
        font-weight: 800;
        line-height: 0.9;
        margin: 0;
      }
      .enter {
        bottom: 10% !important;
      }
    }
    #section05_video {
      height: 100%;
    }
    .section05_img {
      width: 100%;
      height: 30%;
      object-fit: cover;
      object-position: center;
      position: absolute;
      bottom: 0;
      left: 0;
      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: center;
        filter: brightness(0.6);
      }
      #section05_text {
        transition: all 2s ease-in-out;
        position: absolute;
        top: 100%;
        width: 80%;
        height: 30%;
        left: 10%;
        display: grid;
        grid-template-rows: repeat(2, min-content);
        row-gap: 10px;
        justify-items: center;
        align-items: center;
      }

      #section05_img-text {
        transition: all 2s ease-in-out;
        position: absolute;
        bottom: -30%;
        width: 80%;
        left: 10%;
        color: #fff;
        font-size: 36px;
        font-weight: 300;
        text-align: center;
        line-height: 1;

        margin: 0;
      }
      .enter {
        bottom: 30% !important;
      }
    }
  }
}
.section06-container {
  .section-bg {
    filter: brightness(0.6);
  }
  .section-06 {
    #section06_text {
      transition: all 2s ease-in-out;
      padding: 10px 0;
      position: absolute;
      display: grid;
      grid-template-rows: repeat(2, min-content);
      row-gap: 10px;
      justify-content: center;
      justify-items: center;
      align-items: center;
      align-content: center;
      top: -300px;
      left: 0;
      width: 100%;
      height: 300px;
      .title {
        color: #fff;
        width: 90%;
        font-size: 50px;
        text-align: center;
        top: 5%;
        left: 5%;
        font-weight: 300;
        line-height: 0.9;
        margin: 0;
      }
      .subtitle {
        color: #fff;
        width: 80%;
        font-size: 70px;
        font-weight: 800;
        text-align: center;
        top: 20%;
        left: 10%;
        line-height: 1;
        margin: 0;
      }
    }
    .enter {
      top: 0% !important;
    }
  }
}
.section07-container {
  .section-bg {
    left: 0;
    width: 100%;
    filter: brightness(0.7);
  }
  .section07_text {
    width: 100%;
    height: 60%;
    position: absolute;
    display: grid;
    grid-template-rows: repeat(3, min-content);
    justify-content: center;
    justify-items: center;
    align-content: center;
    align-items: center;
    top: 0;
    left: 0;
    z-index: 1;
  }
  .section-07 {
    .title {
      color: #fff;
      width: 90%;
      font-size: 200px;
      text-align: center;
      font-weight: 800;
      line-height: 0.9;
      margin: 0;
    }
    .subtitle {
      color: #fff;
      width: 80%;
      font-size: 50px;
      font-weight: 300;
      text-align: center;
      line-height: 1;
      margin: 0;
    }
    .downgrade {
      transition: all 2s ease-in-out;
      position: absolute;
      bottom: -7%;
      color: #fff;
      width: 80%;
      font-size: 26px;
      font-weight: 300;
      left: 10%;
      margin: 0;
    }
    .enter {
      bottom: 15%;
    }
  }
}
.section08-container {
  .section-bg {
    position: absolute;
    height: 100vh;
    filter: brightness(0.7);
    z-index: 0;
  }
  .section-08 {
    position: absolute;
    display: grid;
    grid-template-rows: repeat(2, min-content);
    row-gap: 10px;
    justify-content: center;
    justify-items: center;
    align-items: center;
    align-content: center;
    width: 80%;
    height: 80%;
    top: 10%;
    left: 10%;
    color: #fff;
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      object-position: center;
      filter: brightness(0.7);
      position: absolute;
      left: 0;
      top: 0;
    }
    .title {
      color: #fff;
      width: 90%;
      font-size: 50px;
      text-align: center;
      font-weight: 800;
      line-height: 1.1;
      z-index: 1;
      margin: 0;
    }
    .subtitle {
      color: #fff;
      width: 80%;
      font-size: 24px;
      font-weight: 300;
      text-align: center;
      line-height: 1.2;
      z-index: 1;
      margin: 0;
    }
  }
}
.section09-container {
  .section-bg {
    position: absolute;
    height: 100vh;
    filter: brightness(0.6);
    z-index: 0;
  }
  .section-09 {
    position: absolute;
    display: grid;
    grid-template-rows: repeat(2, min-content);
    row-gap: 10px;
    justify-content: center;
    justify-items: center;
    align-items: center;
    align-content: center;
    width: 90%;
    height: 80%;
    top: 10%;
    left: 5%;
    color: #fff;
    .title {
      color: #fff;
      width: 90%;
      font-size: 70px;
      text-align: center;
      font-weight: 800;
      line-height: 1.1;
      z-index: 1;
      margin: 0;
    }
    .subtitle {
      color: #fff;
      width: 80%;
      font-size: 36px;
      font-weight: 300;
      text-align: center;
      line-height: 1.2;
      z-index: 1;
      margin: 0;
    }
  }
}
.section10-container {
  .section10-img {
    .section-bg {
      transition: all 6s ease-in-out;
      position: absolute;
      height: 100%;
      width: 100%;
      filter: brightness(0.7);
      left: 0;
      object-fit: cover;
      object-position: 0;
    }
    .enter {
      object-position: 100%;
    }
  }
  .section10-text {
    .section-10 {
      transition: all 2s 3s;
      position: absolute;
      display: grid;
      justify-content: center;
      justify-items: center;
      align-items: center;
      align-content: center;
      width: 80%;
      height: 100%;
      top: 0;
      left: 10%;
      color: #fff;
      opacity: 0;
      filter: blur(20px);
      img {
        filter: brightness(0.8);
        width: 100%;
        height: 300px;
        object-fit: cover;
        grid-column: 1/2;
        grid-row: 1/2;
      }
      .title {
        color: #fff;
        width: 90%;
        font-size: 50px;
        text-align: center;
        font-weight: 800;
        line-height: 0.9;
        grid-column: 1/2;
        grid-row: 1/2;
        z-index: 1;
        margin: 0;
      }
    }
    .enter {
      opacity: 1;
      filter: blur(0);
    }
  }
}
.section11-container {
  .section-bg {
    transition: all 3s ease-in-out;
    filter: brightness(0.7);
    left: 0 !important;
    object-position: 0%;
    width: 100%;
  }
  .enter {
    object-position: 100%;
  }
  .section-11 {
    color: #fff;
    display: grid;
    row-gap: 10px;
    padding: 30px;
    position: absolute;
    width: calc(100% - 60px);
    bottom: 20%;
    left: 0;
    .title {
      z-index: 2;
      width: 80%;
      justify-self: flex-start;
      text-align: left;
      font-size: 44px;
      font-weight: 400;
      margin: 0;
    }
    .subtitle {
      z-index: 2;
      width: 70%;
      justify-self: flex-end;
      font-size: 64px;
      font-weight: 800;
      text-align: left;
      line-height: 1;
      margin: 0;
    }
    .downgrade {
      z-index: 2;
      font-size: 20px;
      width: 70%;
      justify-self: flex-end;
      text-align: left;
      margin: 0;
    }
  }
}
.section12-container { 
  .section-bg {
    transition: all 3s ease-in-out;
    left: 0;
    object-position: 0%;
    width: 100%;
    filter: brightness(0.7);
  }
  .enter {
    object-position: 100%;
  }
  .section12-text {
    .section-12 {
      transition: all 2s 1s ease-in-out;
      display: grid;
      grid-template-rows: repeat(3, min-content);
      row-gap: 10px;
      padding: 20px;
      background: #fff;
      width: 60%;
      height: min-content;
      color: #444;
      z-index: 2;
      position: absolute;
      left: 0;
      bottom: 5%;
      opacity: 0;
      filter: blur(20px);
      .title {
        font-size: 40px;
        font-weight: 300;
        line-height: 0.9;
        margin: 0;
      }
      .subtitle {
        font-size: 60px;
        font-weight: 800;
        line-height: 0.9;
        margin: 0;
      }
      .downgrade {
        font-size: 17px;
        font-weight: 400;
        margin: 0;
      }
    }
    .enter {
      opacity: 1;
      filter: blur(0);
    }
  }
}
.section13-container {
  .section-bg {
    position: absolute;
    height: 100%;
    filter: brightness(0.7);
    left: 0;
  }
  .section-13 {
    color: #fff;
    display: grid;
    height: 100vh;
    grid-template-rows: repeat(2, min-content);
    justify-content: center;
    align-items: center;
    align-content: center;
    justify-items: center;
    row-gap: 10px;
    opacity: 0;
    filter: blur(20px);
    .title {
      z-index: 2;
      width: 80%;
      font-size: 38px;
      font-weight: 800;
      line-height: 1;
    }
    .subtitle {
      z-index: 2;
      width: 80%;
      font-size: 29px;
      font-weight: 300;
      line-height: 0.9;
    }
  }
  #section13_img {
    position: absolute;
    top: -40%;
    left: 15%;
    width: 70%;
    height: 250px;
    object-fit: cover;
    filter: brightness(0.7);
  }
}
.section14-container {
  background: #fff;
  .section-bg {
    height: 90vh;
    position: absolute;
    top: 0;
    left: 0;
    object-fit: cover;
  }
  .section-14 {
    color: #fff;
    width: 100%;
    height: 100vh;
    display: grid;
    grid-template-rows: repeat(2, min-content);
    grid-template-columns: 100%;
    justify-content: center;
    justify-items: center;
    align-content: center;
    align-items: center;
    .subtitle {
      z-index: 2;
      width: 90%;
      font-size: 60px;
      text-align: center;
      font-weight: 300;
    }
    .downgrade {
      z-index: 2;
      width: 90%;
      font-size: 60px;
      text-align: center;
      font-weight: 800;
      line-height: 1;
    }
  }
  #section14_img {
    width: 60%;
    height: 30%;
    position: absolute;
    bottom: 0;
    right: 0;
    object-fit: cover;
    object-position: center;
  }
  .title {
    z-index: 2;
    position: absolute;
    width: 80%;
    left: 0;
    top: -5%;
    font-size: 170px;
    font-weight: 800;
    line-height: 1;
    white-space: nowrap;
    color: #e40524;
  }
}
.section15-container {
  .section-bg {
    height: 100vh;
  }
  .section-15 {
    color: #fff;
    position: absolute;
    row-gap: 20px;
    justify-content: center;
    justify-items: center;
    align-items: center;
    align-content: center;
    width: 80%;
    height: 80%;
    top: 10%;
    left: 10%;
    img {
      width: 100%;
      height: 100%;
      position: absolute;
      left: 0;
      top: 0;
      object-fit: cover;
      object-position: right;
      filter: brightness(0.7);
    }
    .subtitle {
      z-index: 2;
      width: 80%;
      font-size: 50px;
      text-align: center;
      font-weight: 800;
      position: absolute;
      bottom: -50%;
      left: 10%;
    }
    .downgrade {
      z-index: 2;
      width: 80%;
      font-size: 30px;
      text-align: center;
      font-weight: 400;
      line-height: 1;
      position: absolute;
      bottom: -50%;
      left: 10%;
    }
  }
  .section15_img01 {
    background-image: url("../assets/img/03.jpg");
    background-size: 200%;
    background-position: bottom right;
    position: absolute;
    top: 0;
    right: 0;
    width: 40%;
    z-index: 2;
    height: 150px;
    object-fit: cover;
    filter: brightness(0.7);
  }
  .section15_img02 {
    background-image: url("../assets/img/09.jpg");
    background-size: 200%;
    background-position: bottom right;
    position: absolute;
    bottom: 0;
    left: 0;
    width: 40%;
    z-index: 2;
    height: 150px;
    object-fit: cover;
    filter: brightness(0.7);
  }
  .title {
    z-index: 2;
    width: 80%;
    font-size: 40px;
    font-weight: 300;
    line-height: 1;
    align-self: flex-start;
    position: absolute;
    top: 20%;
    left: 10%;
  }
}
.section16-container {
  .section-bg {
    left: 0;
    width: 100%;
    filter: brightness(0.7);
  }
  .section-16 {
    color: #fff;
    width: 80%;
    height: 70%;
    position: absolute;
    top: 10%;
    left: 10%;
    display: grid;
    grid-template-columns: 100%;
    grid-template-rows: min-content min-content 30%;
    row-gap: 20px;
    justify-content: center;
    justify-items: center;
    align-content: flex-end;
    align-items: center;
    .title {
      color: #fff;
      width: 100%;
      font-size: 50px;
      text-align: center;
      font-weight: 800;
      line-height: 0.9;
    }
    .subtitle {
      color: #fff;
      width: 100%;
      font-size: 60px;
      font-weight: 300;
      text-align: center;
      line-height: 1;
    }
    img {
      width: 50%;
      align-self: flex-end;
    }
  }
}
.section17-container {
  background: #e40524;
  display: flex;
  .section-17 {
    display: grid;
    height: 100%;
    grid-template-columns: 100%;
    grid-template-rows: repeat(2, min-content);
    row-gap: 30px;
    justify-content: center;
    justify-items: center;
    align-items: center;
    align-content: center;
    align-self: center;
    .logo {
      width: 60%;
    }
    .bptl {
      width: 40%;
    }
  }
}
@media screen and (max-height: 735px) {
  .section15-container {
    .title {
      font-size: 30px;
    }
    .section-15 {
      .subtitle {
        font-size: 44px;
      }
      .downgrade {
        font-size: 26px;
      }
    }
  }
}
@media screen and (max-width: 378px) {
  .section01-container {
    .section-01 {
      .call {
        font-size: 44px;
        bottom: 40%;
      }
      #section1_citylover {
        font-size: 130px;
        right: -270px;
      }
    }
  }
  .section02-container {
    .section-02 {
      .title {
        font-size: 40px;
      }
      .subtitle {
        font-size: 50px;
      }
      .downgrade {
        font-size: 27px;
      }
    }
  }
  .section03-container {
    .section-03 {
      .subtitle {
        font-size: 25px;
        bottom: 15%;
      }
      .section-03_02 {
        .title02 {
          font-size: 50px;
        }
      }
      .subtitle02 {
        font-size: 25px;
        bottom: 15%;
      }
    }
  }
  .section05-container {
    .section-05 {
      .title {
        font-size: 50px;
      }
    }
  }
  .section06-container {
    .section-06 {
      .title {
        font-size: 40px;
      }
      .subtitle {
        font-size: 60px;
      }
    }
  }
  .section08-container {
    .section-08 {
      .title {
        font-size: 50px;
      }
      .subtitle {
        font-size: 24px;
      }
    }
  }
  .section09-container {
    .section-09 {
      .subtitle {
        font-size: 26px;
      }
    }
  }
  .section10-container {
    .section-10 {
      .title {
        font-size: 50px;
      }
    }
  }
  .section11-container {
    .section-11 {
      .title {
        font-size: 34px;
      }
      .subtitle {
        font-size: 50px;
      }
      .downgrade {
        font-size: 16px;
      }
    }
  }
  .section12-container {
    .section-12 {
      .title {
        font-size: 32px;
      }
      .downgrade {
        font-size: 14px;
      }
    }
  }
  .section13-container {
    .section-13 {
      .title {
        font-size: 38px;
      }
      .subtitle {
        font-size: 26px;
      }
    }
  }
  .section14-container {
    .section-14 {
      .subtitle {
        font-size: 49px;
      }
      .downgrade {
        font-size: 60px;
      }
    }
  }
  .section15-container {
    .title {
      font-size: 30px;
    }
    .section-15 {
      .subtitle {
        font-size: 44px;
      }
      .downgrade {
        font-size: 26px;
      }
    }
  }
}
@media screen and (max-width: 321px) {
  .section01-container {
    .section-01 {
      .call {
        font-size: 40px;
      }
    }
  }
  .section02-container {
    .section-02 {
      .downgrade {
        font-size: 23px;
      }
    }
  }
  .section05-container {
    .section-05 {
      .title {
        font-size: 46px;
      }
      .subtitle {
        top: 21%;
      }
    }
  }
  .section06-container {
    .section-06 {
      .subtitle {
        font-size: 50px;
      }
    }
  }
  .section07-container {
    .section-07 {
      .subtitle {
        font-size: 40px;
      }
    }
  }
  .section10-container {
    .section-10 {
      .title {
        font-size: 46px;
      }
    }
  }
  .section11-container {
    .section-11 {
      .title {
        font-size: 32px;
      }
    }
  }
  .section12-container {
    .section-12 {
      .subtitle {
        font-size: 50px;
      }
    }
  }
  .section13-container {
    .section-13 {
      .title {
        font-size: 32px;
        bottom: 63%;
      }
      .downgrade {
        font-size: 20px;
      }
    }
  }
  .section15-container {
    .title {
      font-size: 26px;
    }
    .section-15 {
      .subtitle {
        font-size: 40px;
      }
      .downgrade {
        font-size: 24px;
      }
    }
  }
}
</style>
