---
title: "Can't install or run Ubuntu from USB"
date: 2015-03-17
forum: Installation &amp; Upgrades
---

### Post by hamilton-sanch on 2015-03-17
So I was using ubuntu for some time and for some reason today while I was installing a program with wine it decided to crash on me.  Before the crash, any command typed in the terminal gave me a message saying segmentation fault. After that I tried booting up my system again and it's a no go.

I decided to start fresh and created a bootable USB from a windows laptop I borrowed. I booted from USB and got to the ubuntu menu just fine. The problem is when I choose either to "try Ubuntu" or "install Ubuntu" it seems like it's going to do something, then it leads me to a screen that I can only assume is a crash. Its a pretty pattern to say the least, but definitely not what I want.

I'm running an older Asus laptop, pre-windows 8 I haven't tried a CD since I don't have any on hand at the moment. Is there an easy fix to this? I'd like my laptop working again soon.

---

### Post by kc1di on 2015-03-17
Hi hamilton-sanch  and Welcome to Ubuntu,

Give us a little more info on your machine.  Especially the video card it uses , if it's an nvidia card you may have to boot with nomodeset parameter to get it to work first time.

---

### Post by hamilton-sanch on 2015-03-17
The computer is an Asus republic of gamers, can't remember the exact model at the moment. Graphics card is Nvidia GeForce 360M. Processor is an Intel i5.

---

### Post by kc1di on 2015-03-17
Ok the reason your having the problem is the nvidia card.

you will have to use nomodeset the first time you boot live, and install the Nvidia driver after you have installed the system.

you can set nomodeset by hitting the tab key just as the live session begins to boot , when the new page comes up hit the F6 key and select nomodeset then hit escape key and then enter.  

It will boot in low graphics mode but will allow you to install the system.

Then on first boot you'll need to again boot with nomodeset and when it boots up use the additional driver tool for in software center > edit >Software Sources > Additional drivers.  install the recommended driver from there and reboot.  you should be good to go after that.  Good Luck :)

NOTE:  the reason you have to do this is because of nvidia's licensing does not allow Ubuntu to ship with those drivers installed. In other words they are propitiatory and can't be modified by Ubuntu.

---

