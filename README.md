# nice!view with cats

The nice!view is a low-power, high refresh rate display meant to replace I2C OLEDs traditionally used.

This shield requires that an `&nice_view_spi` labeled SPI bus is provided with _at least_ MOSI, SCK, and CS pins defined.

![Crkb with nice!view](/images/image1.png)

## Usage

#### `config/west.yml`
``` yml
manifest:
  remotes:
    - name: zmkfirmware
      url-base: https://github.com/zmkfirmware
    - name: s6t
      url-base: https://github.com/s6t
  projects:
    - name: zmk
      remote: zmkfirmware
      revision: main
      import: app/west.yml
    - name: zmk-shield-nice-view-cats
      remote: s6t
      revision: main
  self:
    path: config
```

#### `build.yaml`
``` yml
include:
  - board: nice_nano_v2
    shield: corne_left nice_view_adapter nice_view_cats
  - board: nice_nano_v2
    shield: corne_right nice_view_adapter nice_view_cats
```