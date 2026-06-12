---
title: "Ubuntu 12.0.4 Installation / Bootup issues?"
date: 2012-07-11
forum: Installation &amp; Upgrades
---

### Post by BraidenS on 2012-07-11
Hello everyone. I found this forum and thought it looked like a very helpful place. I'm hoping someone can help me out.

I am a new Linux user and recently burned Ubuntu 12.0.4 to a 700MB / 80m cdr. Upon booting from the disc I get a blue screen 80% of the time. If I keep restarting eventually I get it to boot and install. The installation runs smoothly. However, after restarting nearly half of the time I get a blue screen with the words "Not Support" in the top right hand corner of my screen.

Now, I assume this is a resolution/graphics card/monitor problem but I am lost in trying to fix it. My graphics card is updated and the computer is fairly new. Can someone please help.

Display Adapters: 
NVIDIA GeForce 8200
NVIDIA GeForce 9600 GT

Monitor:
Olevia 23" LCD

Thanks everyone

---

### Post by jmfal on 2012-07-11
Welcome to Ubuntu

You may have a graphics card problem,  lets see if you have a working ubuntu

Restart>>  at bios/boot menu screen press and hold down the shift key, this should get you to the grub screen, >>>select recovery kernal, press enter>>select resume normal boot >> and this should get you to the login screen.

---

### Post by drs305 on 2012-07-11
If using the LiveCD, check out these options during boot. Video problems are often resolved by using the 'nomodeset' option until you can boot and install the appropriate drives from the Ubuntu repositories. There are other options available as well.

[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

---

### Post by OM55 on 2012-07-11
To reiterate what the others wrote before me, I also think it is a video driver issue. Especially since you listed Nvidia as your graphic card. There are many issues with Nvidia drivers (see also the recent public exchange of 'adjectives' between Linus Torvalds, creator of Linux and Nvidia corporation).

As it happens the proprietary Nvidia driver is often very unstable and it seems that every time a new version is out, they fix some of the old bugs but bring in new ones... However the open source NVidia drivers and others (all available for Linux) work generally very well, as long as you do not intend to play extremely high speed 3D computer games...

What may happen in your case is that the Ubuntu Linux installer automatically selects and installs the Nvidia proprietary driver, and it crashes. If you follow the instructions in the previous replies above,  you should be able to load the system without the proprietary Nvidia driver and get to a working desktop. If that works, to avoid installing the proprietary Nvidia driver later on. 
Keep in mind that unless you install some Nvidia driver (open source or other) you will probably not have graphic features like Open GL, which are required for programs like Google Earth and Compiz.

Another way to do so: When you start a fresh Ubuntu installation, on of the first screens will ask your permission to install "3rd party proprietary drivers". Simply uncheck that box and (if the video driver is the problem) you should be fine.

---

