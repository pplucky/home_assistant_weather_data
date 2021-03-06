# Weather data

![Validate with hassfest](https://github.com/Danielhiversen/home_assistant_weather_data/workflows/Validate%20with%20hassfest/badge.svg)
[![GitHub Release][releases-shield]][releases]
[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/custom-components/hacs)

Replaces the old yr sensor.

Install it as a custom component or use https://hacs.xyz/docs/faq/custom_repositories.


To migrate from the old yr sensor, replace `- platform: yr` with `- platform: weather_data`. All sensor entities should be unchanged.

The `weather_data` platform uses [met.no](https://www.met.no/) as a source for current
meteorological data for your location. The weather forecast is delivered by the
Norwegian Meteorological Institute and the NRK.

To add the weather data to your installation,
add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
sensor:
  - platform: weather_data
```

```yaml
name:
  description: Additional name for the sensors.
  required: false
  type: string
  default: yr
forecast:
  description: If you want to get forecast data instead of the current weather data, set this to the number of hours that you want to look into the future.
  required: false
  type: integer
monitored_conditions:
  description: Conditions to display in the frontend.
  required: false
  type: list
  default: symbol
  keys:
    symbol:
      description: A symbol for the current weather.
    temperature:
      description: The current temperature.
    humidity:
      description: The relative humidity.
    fog:
      description: Fog.
    pressure:
      description: The sea-level air pressure in millibars.
    precipitation:
      description: The precipitation.
    dewpointTemperature:
      description: The dew point temperature.
    windSpeed:
      description: The wind speed.
    windDirection:
      description: Where the wind is coming from in degrees, with true north at 0° and progressing clockwise.
    cloudiness:
      description: The cloudiness.
    lowClouds:
      description: Low cloud level.
    mediumClouds:
      description: Medium cloud level.
    highClouds:
      description: High cloud level.
latitude:
  description: Manually specify latitude.
  required: false
  type: float
  default: Provided by Home Assistant configuration.
longitude:
  description: Manually specify longitude.
  required: false
  type: float
  default: Provided by Home Assistant configuration.
altitude:
  description: Manually specify altitude.
  required: false
  type: float
  default: Provided by Home Assistant configuration.
```

A full configuration example can be found below:

```yaml
# Example configuration.yaml entry
sensor:
  - platform: weather_data
    name: Weather
    forecast: 24
    monitored_conditions:
      - temperature
      - symbol
      - precipitation
      - windSpeed
      - pressure
      - windDirection
      - humidity
      - fog
      - cloudiness
      - lowClouds
      - mediumClouds
      - highClouds
      - dewpointTemperature
```

[Support the developer](http://paypal.me/dahoiv)

[releases-shield]: https://img.shields.io/github/release/Danielhiversen/home_assistant_weather_data.svg?style=popout
[releases]: https://github.com/Danielhiversen/home_assistant_weather_data/releases
