---
title: "Installation Problems with Ubuntu 13.10"
date: 2014-09-27
forum: Installation &amp; Upgrades
---

### Post by Austin_McCreery on 2014-09-27
I am trying to download Ubuntu 13.10 from the DVD disk I got out of the  Ubuntu Unleashed book I bought, and it keeps getting stuck on  "configuring bcmwl-kernel-source" why is this happening, and what should  I do to fix it?

---

### Post by mörgæs on 2014-09-27
Please stop multiposting. I have jailed your two duplicate posts.

---

### Post by slickymaster on 2014-09-27
Why are trying yo install Ubuntu 13.10? It's EOL since July 17, 2014.

I recommend you to instead go with Ubuntu 14.04 LTS (supported until April 2019) or 12.04.5 LTS (supported until April 2017).

---

### Post by Austin_McCreery on 2014-09-27
i meant 13.10. im sorry

---

### Post by slickymaster on 2014-09-27
Please see [post #3]("http://ubuntuforums.org/showthread.php?t=2245987&p=13130553&viewfull=1#post13130553").

As for the reason why you getting stuck getting stuck on "configuring bcmwl-kernel-source", and even though I'm no expert in the subjuect, I'd say it could be a conflict with the native b43 driver. During installation, don't select the option to "Download Updates while installing". This will prevent the bcmwl-kernel-source package and other proprietary drivers from being downloaded and installed. Note that this will also cause the firmware to not download, which you can install later when the installation is finished.

Later on to install the required firmware, run the following command in a terminal window:```
sudo apt-get install linux-firmware-nonfree
```

---

