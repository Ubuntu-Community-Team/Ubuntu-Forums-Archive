---
title: "Colors in video"
date: 2009-07-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Joe_Bishop on 2009-07-05
I have a strange problem while video playback, just take a look.

First, how it should look like (made with totem video shot tool)
[IMG]http://img-fotki.yandex.ru/get/3502/fork-posix.0/0_25d2c_d87986b6_orig[/IMG]

Second, how it looks like during playback:
[IMG]http://img-fotki.yandex.ru/get/3601/fork-posix.0/0_25d2d_631d6501_orig[/IMG]

Actually, all players I've installed have this problem: Totem, VLC, Mplayer. Any ideas?

---

### Post by taavikko on 2009-07-05
If using totem, try switching video-output module from "gstreamer-properties"
And for other players, experiment with video-output modules from their settings.

---

### Post by Joe_Bishop on 2009-07-05
Hm, strange. Reset Edit->Preferences->Display->Hue to default value (to the middle), and all players begin to show correctly.

---

### Post by tim1 on 2009-07-05
There is probably something wrong with the color settings of Totem. Go to preferences and reset the color sliders.

---

### Post by budluva04 on 2009-07-05
if your an nvidia user its a known bug...

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/395476]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/395476")

---

### Post by soapytheclown on 2009-07-05
i had the same problem using nvidia too, to get around it temporarily ive done this:
1. run gstreamer-properties
2. on the video tab change the default output plugin to be "X Window System (No Xv)"

that works for me

---

### Post by lithorus on 2009-07-06
> **soapytheclown said:**
> i had the same problem using nvidia too, to get around it temporarily ive done this:
1. run gstreamer-properties
2. on the video tab change the default output plugin to be "X Window System (No Xv)"

that works for me
Just makes the playback performance horrible.

---

### Post by psyke83 on 2009-07-06
> **soapytheclown said:**
> i had the same problem using nvidia too, to get around it temporarily ive done this:
1. run gstreamer-properties
2. on the video tab change the default output plugin to be "X Window System (No Xv)"

that works for me

FYI: that disables hardware accelerated playback, which means that video will be pixelated and lacking vertical synchronization. Not exactly an ideal solution.

---

### Post by soapytheclown on 2009-07-06
well works fine for me watching 720p videos at 1920 x 1080 and whilst its not an idea solution if you read what id written im only doing it 'to get around it temporarily', if it works for you great if it doesn't wait for the official fix

---

### Post by psyke83 on 2009-07-06
> **soapytheclown said:**
> well works fine for me watching 720p videos at 1920 x 1080 and whilst its not an idea solution if you read what id written im only doing it 'to get around it temporarily', if it works for you great if it doesn't wait for the official fix

Right. Totem doesn't handle video playback without acceleration (video skips a lot), so a better alternative is to use another player such as mplayer (mplayer -vo x11).

---

