---
title: "dvd iso images and totem 2.24.3"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by Piviul on 2008-11-21
Hi, I've just upgraded ubuntu 8.04 to 8.11 and I have a new little problem. In ubuntu 8.04 double clicking on a dvd iso images totem I was able to see the dvd video on totem, now totem start but doesn't show the video. I have forgotten to install some package? Someone can explain me how totem was able to show the video without mounting the iso image and why now that doesn't work any more?

Thank you very much

Piviul

---

### Post by taurus on 2008-11-21
Does vlc play that iso video file?

```
sudo apt-get update
sudo apt-get install vlc
vlc *filename.iso*
```

---

### Post by Piviul on 2008-11-22
Yes vlc does, but I have another problem using vlc: in Ubuntu 8.11 I can't use Xv in X window because ati driver doesn't seem to support it. In totem I have disabled Xv from gstreamer properties but seems that vlc doesn't read the gstremer settings so please do you know  how can I tell vlc don't use Xv?

Otherwise there is a way to use Xv in a Radeon HD 2400 PRO?

Thank you very much.

Piviul

---

### Post by taurus on 2008-11-22
Look under Tools -> Preferences -> Video -> Output.

---

### Post by Piviul on 2008-11-22
Thank you very much, now vlc shows the dvd iso images... so there is no way to see them on totem and/or to set up my video card to support use Xv?

Thank you very much

Piviul

---

### Post by mc4man on 2008-11-22
I don't know about ati, am using nvidia
You might want to try totem-xine and see if you have any luck.
```
sudo apt-get install totem-xine libxine1-ffmpeg
```

Then right click on an iso -> open with -> open with other application. Locate and click on Movie Player (Xine)

If it works out then r. click on the .iso again -> properties -> open with and choose Movie Player (Xine). If not there click the 'add' button and you should find it.

As far as totem-gstreamer, dvds, and by extension an .iso, here's a notation from the current totem source that sums it up very well.

> # only totem-xine can play DVDs and VCDs satisfactorily  (for now)

---

