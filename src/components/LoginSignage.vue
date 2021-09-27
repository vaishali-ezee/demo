<template>
  <div class="yc-brand-band" id="login-signage-bg">
    <div class="yc-row yc-fill-height yc-justify-end yc-align-center">
      <div class="yc-col yc-col-6">
        <div class="yc-card yc-text-align_center yc-text-color_black">
          <div class="yc-text-heading_large yc-text-heading_color yc-p-bottom_24 yc-p-top_24">
            {{ ycTextData.title }}
          </div>
          <div class="yc-text-heading_medium">
            <div>{{ ycTextData.subtitle1 }}</div>
            <div>{{ ycTextData.subtitle2 }}</div>
          </div>
          <div class="yc-p-top_48">
            <a :href="loginUrl" class="yc-button">
              <span
                class="material-icons md-18 yc-icon-font_size yc-m-right_8 yc-m-left_4"
              >
                login
              </span>
              <span class="yc-text-title">
                {{ ycTextData.loginButtonText }}
              </span>
            </a>
          </div>
        </div>
      </div>
    </div>
    <footer class="yc-footer-signage">
      <div class="yc-card">
        <div class="yc-text-body yc-p-bottom_12">
          {{ ycTextData.footerText }}
        </div>
        <a :href="`mailto:${ycTextData.mailto}`" class="yc-card__link yc-text-title" target="_blank">
          <span class="yc-box_content">
            <span class="material-icons yc-m-right_8">mail_outline</span>
            <span>{{ ycTextData.mailto }}</span>
          </span>
        </a>
      </div>
    </footer>
  </div>
</template>

<script>

import configs from '../config'
import locale from '../locales'

export default {
  name: 'LoginSignage',
  props: {
    env: {
      type: String,
      required: true
    },
    language: {
      type: String
    }
  },

  data() {
    return { 
      loginUrl: configs(this.env).signageURL + window.location.href,
      ycTextData: {
        loginButtonText: locale[this.language].commonText.loginButtonText,
        title: locale[this.language].signage.title,
        subtitle1: locale[this.language].signage.subTitle1,
        subtitle2: locale[this.language].signage.subTitle2,
        footerText: locale[this.language].signage.footerText,
        mailto: 'signage@yanolja.com',
      },
    }
  },
}
</script>
