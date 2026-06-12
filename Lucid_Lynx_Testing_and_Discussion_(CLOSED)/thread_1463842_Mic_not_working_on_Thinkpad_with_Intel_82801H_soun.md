---
title: "Mic not working on Thinkpad with Intel 82801H sound card"
date: 2010-04-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by andresmh on 2010-04-27
This is an [inherited regression]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409819") from Karmic that I had hoped would be fixed in Lucid but, sadly, it is not. I think the problem is that Ubuntu is only recognizing the green jack on the side of my computer as the only sound input and it is not recognizing the built-in mic on the chasis.

Here are the specs of my Thinkpad X300.

```

$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

$cat /proc/asound/card*/codec\#*|grep -i codec
Codec: Analog Devices AD1984A

$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

```

By the way, the subject of this post is inspired by [http://lunduke.com/?p=1075](http://lunduke.com/?p=1075)

---

