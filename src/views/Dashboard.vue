<template>
  <div id="App">
    AQI: {{ aqi }}
    <br>
    CATEGORY: {{ category }}
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  data () {
    return {
      aqi: null,
      category: null,
      health_recommendation: null
    }
  },
  mounted () {
    axios.get('https://api.breezometer.com/air-quality/v2/current-conditions?lat=48.857456&lon=2.354611&key=255c750634c243d39c6a891fa5532b51&features=breezometer_aqi,local_aqi,health_recommendations,sources_and_effects,pollutants_concentrations,pollutants_aqi_information')
      // eslint-disable-next-line no-return-assign
      .then(response => (
        // eslint-disable-next-line no-sequences
        this.aqi = response.data.data.indexes.baqi.aqi,
        this.category = response.data.data.indexes.baqi.category))
  }
}
</script>
