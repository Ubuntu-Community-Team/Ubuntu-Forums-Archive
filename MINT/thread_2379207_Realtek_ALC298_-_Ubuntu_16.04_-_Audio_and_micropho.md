---
title: "Realtek ALC298 - Ubuntu 16.04 - Audio and microphone not working"
date: 2017-12-02
forum: MINT
---

### Post by fbgolly on 2017-12-02
Hi,


I installed Linux Mint (Cinnamon) based on Ubuntu 16.04 and I have some issue with my sound card Realtek ALC298.
System audio not working, even the "test sound" from the audio settings. but with Spotify and browser (like netflix) it working.
Internal microphone not working.


This is my audio card info:


cat /proc/asound/cards
```

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xb4220000 irq 289

``` 


cat /proc/asound/card0/codec* | grep Codec
```

Codec: Realtek ALC298
Codec: Intel Kabylake HDMI

```


cat /proc/asound/card0/pcm0c/info
```

card: 0
device: 0
subdevice: 0
stream: CAPTURE
id: ALC298 Analog
name: ALC298 Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1

```


I try to edit some configuration with alsamixer, un-muting/muting device, disabling/enabling "auto mute" but with no effect
[IMG]http://oi67.tinypic.com/2e30kmx.jpg[/IMG]


I also try to change device profile with pavucontrol setting "Analog Stereo Deplex" with no effects.
I change the model in /etc/modprobe.d/alsa-base.conf using base, laptop-amic and other values but nothing works.
I try to download the latest Realtek driver from [http://www.realtek.com.tw/Downloads/downloadsView.aspx?Conn=4&DownTypeID=3&Langid=1&Level=5&PFid=5&PNid=13](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Conn=4&DownTypeID=3&Langid=1&Level=5&PFid=5&PNid=13) and installing it but with no results...


I can't understand how to fix this problem, someone can help me?

---

### Post by coffeecat on 2017-12-02
*Thread moved to the **MINT** sub-forum.*

---

