---
title: "Can't start X 2 videocards"
date: 2006-04-25
forum: Installation &amp; Upgrades
---

### Post by GekkeHenk on 2006-04-25
I got two videocards, one on-board videocard on which no monitor is installed and one AGP videocard which contains a Geforce 6600 GT.
I just installed ubuntu after not used linux in about 3 years. The install went fine but X won't start. After the install it tried to start X but then my screen got weird and my monitor said: Non-preset mode.

After I did a reconfigure and automaticcaly tried to configure xorg.conf. It already said I have a geforce 6600, but when I complete the configuration it still won't start?

---

### Post by dermotti on 2006-04-25
Well first of all ide just disable the onboard video.

Then, i would make sure you download the **nvidia-glx** package

after that run **sudo dpkg-reconfigure xserver-xorg** and select **nvidia** as yoru driver. Then reboot and you shoul dhave X after that.

---

### Post by GekkeHenk on 2006-04-25
Thank you very much, I installed the nvidia drivers and now I'm online at my own Ubuntu installation :)

---

