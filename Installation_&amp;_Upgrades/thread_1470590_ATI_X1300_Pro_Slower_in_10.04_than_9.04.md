---
title: "ATI X1300 Pro Slower in 10.04 than 9.04"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by jelofson on 2010-05-03
Just did a fresh install of 10.04. I am using the Ati opensource driver. I noticed in a game that I was getting significantly lower frame rates now. Actually about 1/2 that of 9.10 

Anyone thing of a reason for that? I was using the opensource driver in 9.10 too. glxgears gives 1/2 the fps I used to get. 

I did search around a bit to see if I could find any answers. 

Thanks,

---

### Post by jelofson on 2010-05-03
Found out that this is related to the Kernel Mode Setting (KMS) and ATI drivers in 10.04

[http://www.phoronix.com/scan.php?page=article&item=ati_ubuntu_kmsums&num=1](http://www.phoronix.com/scan.php?page=article&item=ati_ubuntu_kmsums&num=1)

To fix this (temporarily) I added an option to my boot menu. I have dual boot so it was easy to get to the the grub boot screen and edit the main entry.

The boot option I set was 
radeon.modeset=0

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I hope this helps someone else.
I believe you have to do this each boot, or there are other options too.

Jon

---

### Post by insaini on 2010-05-06
I just figured this out myself..

you can edit /etc/default/grub 

add 'nomodeset' to the kernel options .. standard options are 'quiet splash'  .. so make it 'quiet splash nomodeset'

then exit and do an sudo update-grub..


its a fix .. you wont get plymouth on startup but atleast you can login..

---

### Post by boombox1387 on 2010-06-08
> **insaini said:**
> I just figured this out myself..

you can edit /etc/default/grub 

add 'nomodeset' to the kernel options .. standard options are 'quiet splash'  .. so make it 'quiet splash nomodeset'

then exit and do an sudo update-grub..


its a fix .. you wont get plymouth on startup but atleast you can login..

Thanks so much for this!  3d/composited graphics were rendering so slowly that my computer was unusable unless I switched to Metacity, but I was finding it really hard to live without Compiz. (I need my screen corner shortcuts!)  Turning off KMS seemed to fix things on my Radeon x1300.

---

