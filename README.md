# UniSolder - Mini
### Universal soldering controller

`Fork of the original Unisolder, meant to be a smaller more portable version of the original (power supply not contained in enclosure)`

Control almost any low voltage soldering instrument

Attempt to build the most universal soldering controller possible. It can drive any low voltage (upto 24V) iron with thermocouple or resistive sensor, in series with the heater, or separate.

### Features
- power: 12-24V, AC or DC (24V 6A toroidal transformer is the best possible power source)
- automatic 1/2, 1/4 and 1/8 power selection, so only simple single winding 24V transformer can drive all the instruments, from the smallest JBC Nano, to the largest JBC C245.
- 2 separate heater control channels
- 2 independent sensor inputs
- current source on any sensor input 3uA - 12mA, with 2 bands (x1, x16) and 256 steps per band
- flexible differential amplifier input selection
- amplifier gain from 0 to 750 in 256 steps
- negative offset selection in 1024 steps
- resistive instrument identification (upto 625 different instruments can be identified by 2 resistors in the connector)
- polynomial floating point voltage/resistance to temperature calculation
- wave shaping to filter out the inductive peaks from series sensor signal
- PID control with power limit
- isolated USB port for firmware updates and live data
- 128x64 OLED display with rich user interface.

### Tested soldering instruments
- HAKKO T12/T15 (series TC)
- HAKKO FX8801 (PTC)
- PACE TD100 (series TC, the controller also uses the cold junction sensor in the iron's handle)
- PACE TD200 (series TC, the controller also uses the cold junction sensor in the iron handle)
- JBC C245 (series or separate TC, depends on connection)
- JBC C210 (series TC)
- JBC Microtweezers (2 separate heaters, each with series TC)
- JBC C105 (series TC)
- WELLER WSP80 (PTC) (This iron was sent to me by a reader of the thread for a previous version of the controller. Thanks, Jaroslaw)
- WELLER WMRT (separate TC)
- ERSA RT80 (series PTC/heater resistance)
- various chinese cheap irons with separate TC

### Working example videos
- JBC C245: https://www.youtube.com/watch?v=oTdQB4ywDOA&feature=youtu.be
- JBC C210: https://www.youtube.com/watch?v=iyz-EDf-JaY&feature=youtu.be
- T12, JBC C210, JBC Microtweezers: https://www.youtube.com/watch?v=-f0KSU0PJzc&t=70s
- Chinese T12: https://www.youtube.com/watch?v=u588sh-4thg&feature=youtu.be
- Weller WSP80: https://www.youtube.com/watch?v=gd_8w7l8_Bo&feature=youtu.be
- Weller WMRT: https://www.youtube.com/watch?v=eHNJuQEw6XU&feature=youtu.be

### Additional resources
- Valerio made a great git repo with plenty ot usefull information and notes [here](https://github.com/valerionew/unisolder-notes)
- There is a really big forum thread for this project, where it all started [here](http://dangerousprototypes.com/forum/index.php?topic=7218.0)

## Calibration procedure
- Connect a resistor with well known resistance (0.1%) of around 10ohm between SENSEA and Vout1-
- Go to "CALIBRATION" submenu
- Adjust the calibration trimmer until you get value of "R" as close as possible to the resistance of the resistor, multiplied by 100 (1000 for 10ohm resistor).

## Connections to different tips/irons

### 1. HAKKO T12:
 - Outer shell, and heater negative (middle) terminal connected together to Vout1- and EARTH
 - heater positive (bottom terminal) connected to Vout1+ and SENSEA
 - 1k resistor between ID and Vout1-
 - 5.6k resistor between ID and Vout2-

### 2. HAKKO FX8801, HAKKO 907 (original, with PTC sensor):
- Outer shell, PTC negative  and heater negative connected to EARTH, Vout1- and SENSEB
- Heater positive connected to Vout1+
- PTC positive  connected to SENSEA
- 1k between ID and Vout1-
- 820ohm between ID and Vout2-

### 3. JBC C245:
 - Outer shell (green wire) connected to EARTH and SENSEB
 - Heater positive(red wire) connected to Vout1- and SENSEA
 - Heater negative(blue wire) connected to Vout1+
 - 150ohm between ID and Vout1-
 - 5.6k between ID and Vout2-

### 4. JBC C210:
 - Outer shell (green wire) connected to EARTH and SENSEB
 - Heater negative (middle terminal, blue wire) connected to Vout1-
 - Heater positive (smaller terminal, red wire) connected to Vout1+ and SENSEA
 - 3.0k between ID and Vout1-
 - 5.6k between ID and Vout2-

### 5. JBC C105/C115:
 - Outer shell (green wire), connected to EARTH
 - Heater negative (blue wire), connected to Vout1-
 - Heater positive (red wire), connected to Vout1+ and SENSEA
 - 3.0k between ID and Vout1-
 - 1.0k between ID and Vout2-

### 6. JBC Microtweezers:
 - Outer shell of both tips (green wire) connected to EARTH
 - Heater 1 negative (blue wire) connected to Vout1-
 - Heater 1 positive (red wire) connected to Vout1+ and SENSEA
 - Heater 2 negative (brown wire) connected to Vout2-
 - Heater 2 positive (yellow wire) connected to Vout2+ and SENSEB
 - 1.0k between ID and Vout1-

### 7. WELLER WSP80:![License CC-BY-4.0](https://img.shields.io/badge/License-CC--BY--4.0-green.svg)
- Outer shell, PTC negative  and heater negative (white, black and brown wires) connected to EARTH, Vout1- and SENSEB
- Heater positive (blue wire) connected to Vout1+
- PTC positive (red wire) connected to SENSEA
- 120ohm between ID and Vout1-
- 5.6k between ID and Vout2-

### 8. ERSA RT80:
- Outer shell and Heater/PTC negative (pink and white wires) connected to EARTH, Vout1- and SENSEB
- Heater/PTC positive (black wire) connected to Vout1+ and SENSEA
- 300ohm between ID and Vout1-
- 110ohm between ID and Vout2-


## Licence
<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
