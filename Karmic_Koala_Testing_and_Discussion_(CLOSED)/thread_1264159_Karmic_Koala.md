---
title: "Karmic Koala"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sin@Sin-Sacrifice on 2009-09-11
So yeah, decided to try out the new Ubuntu and got as far as the choice between Try and Install. I tried Try and it dropped to a login prompt and I couldn't figure out a working login. So I tried install and got an error and it wouldn't do anything. I had to add the option to all linux installs and live cd options to pci=nomsi so it would look for sata but pressing F6 doesn't allow me to do so. Fairly new hardware... anyway, got it running in virtualbox with no problems. Drawing a blank here. If you need the output from the install I forgot to copy it down but let me know if you need it.

---

### Post by VMC on 2009-09-11
It works in VM should be a good indicator that the cd works. Or did you just use the ISO? Is so, try and use the cd fro vm and see if any differance.

Also, what video chip - ATI, Intel , etc.

---

### Post by Sin@Sin-Sacrifice on 2009-09-11
It was from a cd, also mounted the iso image and worked in vm. On-board GeForce 8200 chipset. Thanks for the fast reply by the by.

---

### Post by VMC on 2009-09-12
You could try this. Boot karmic livecd, select F6 other options, then add to the end of line nomodeset single.

Once boot up to recovery menu, select netroot. From root prompt (#) install your nVidia driver found [here]("http://packages.ubunut.com/ko/karmic/nvidia-glx-173").

OR from the same root prompt type ```
Xorg -configure
``` then ```
mv xorg.config.new /etc/X11/xorg.conf
``` then using vi editor do this: vi /etc/X11/xorg.conf. Now your into vi. find the section "Device", then find Driver. replace whatever is in between the "" with "visa".

Actually you can use gedit to do all the stuff above. I'm more comfortable using vi. At any rate see if using vesa driver will allow you to continue to bootup livecd.

Edit: I have an Intel integrate video so what I'm suggesting is a stab in the dark. Maybe someone will come along that has an nVidia to help.

---

### Post by Sin@Sin-Sacrifice on 2009-09-12
Hey thanks again VMC... just snuck out of the bedroom to catch a smoke but my girl's not feeling too good so I can't try it until morning but will do then. This hardware has been a lot of trouble for me so hoping to help out a bit. Oh and I've come to like nano for text. Anyway... will be back in the morning to take a stab at it.

---

### Post by Sin@Sin-Sacrifice on 2009-09-12
When I press F6 I get a drop-down menu and that option is not in there. Is there a way I can bypass that and add a custom option? The error I got upon attempted install is an xsession error and more than likely due to the video drivers though.

---

### Post by VMC on 2009-09-12
> **Sin@Sin-Sacrifice said:**
> When I press F6 I get a drop-down menu and that option is not in there. Is there a way I can bypass that and add a custom option? The error I got upon attempted install is an xsession error and more than likely due to the video drivers though.

Forget the drop down. If you notice their is the kernel line behind it. Just click on the screen behind it and click "end", then add whatever, and off you go.

---

