---
title: "aplay works, but not rhythmbox: How to set device"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by krausest on 2008-10-12
Dear all,

sound output works fine if I say:
aplay -D surround51 test.wav
It fails when I do not set the device:
stef@hape:~/mp3$ aplay test.wav 
Playing WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
ALSA lib pcm_pulse.c:629:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

aplay: set_params:1015: Unable to install hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  S16_LE
SUBFORMAT:  STD
SAMPLE_BITS: 16
FRAME_BITS: 32
CHANNELS: 2
RATE: 44100
PERIOD_TIME: 125000
PERIOD_SIZE: (5512 5513)
PERIOD_BYTES: 22050
PERIODS: 4
BUFFER_TIME: 500000
BUFFER_SIZE: 22050
BUFFER_BYTES: 88200
TICK_TIME: [0 0]

Similarly it fails for some other devices. Rhythmbox and the Sound preferences don't work either but I guess they'd work if the default device was set correctly.

How do I configure which pcm device (not sound card, there's just one card) alsa should use?

stef@hape:~/mp3$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

stef@hape:~/mp3$ aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=Intel,DEV=0
    HDA Intel
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

front and some surround configurations do not work.

---

