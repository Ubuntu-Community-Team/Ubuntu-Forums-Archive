---
title: "Ubuntu Dapper Installation Problem"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by Elmin on 2006-07-22
Hi,

I am having problem with my installation of Ubuntu Dapper. I just received my CD from ShipIt. I put in the cd and did a check sum and everything is ok. I went ahead to reboot it and restart the PC and then choose Install option. It boot up fine and then the graphic get twisted. I can do a Ctrl Alt F1 to go into the command line of it. I think the x-server cannot start. But after that I do not know how to continue the installation of the Ubuntu Dapper. 

My PC spec are as below..

Dell Dimension 5100
P4 2.8 Ghz
80 GB SATA HDD as primary
300 GB SATA HDD as secondary
Nvidia 6800 PCIe graphic card
Integrated sound card and network card.

I am still using Breezy and have not encountered this problem. Is there any way to go about this ? 

Thanks

@@ Elmin

p/s I'm trying to solve this issue by this week...

---

### Post by Ziox on 2006-07-22
you can use this command to upgrade from breezy to dapper without any discs:

gksu update-manager -d

as for you cd's problem, are you talking about the live cd or the alternative cd?

---

### Post by Elmin on 2006-07-22
Hi Ziox,

Regarding the CD, I'm not sure myself. I ordered it from ShipIt and received it on Wednesday. I think it should be the live CD. 

Does the "gksu update-manager -d" take a long time to download ? If I want to do a clean install with the CD, is there no other option to install from the Live CD ?

Thanks,

@@ Elmin

---

### Post by Ziox on 2006-07-22
> **Elmin said:**
> Hi Ziox,

Regarding the CD, I'm not sure myself. I ordered it from ShipIt and received it on Wednesday. I think it should be the live CD. 

Does the "gksu update-manager -d" take a long time to download ? If I want to do a clean install with the CD, is there no other option to install from the Live CD ?

Thanks,

@@ Elmin

well...gksu update-manager -d can take a long time, because it need to update just about everything on your system.  As for a clean install (which is what i recommand), you can download the alternative cd from ubuntu.com.  The alternative cd is a text-based installation process.  Though it may sound scary, it is really easy to use. And it is faster. I've always trusted the alternative cd more than the live CD. The download is something like 600 MB for the .iso.  

BTW, i should've asked this b4, how is the graphics twisted when you boot up? And after you switched to console #1 (Ctrl + Alt + F1), did you try to swithc back to the graphic console? (Ctrl + Alt + F7).  Also, Ctrl + Alt + Backspace forces X to restart, which may solve the problem.

EDIT: try cycling to every virtual console (Ctrl + Alt + F1 to F7), i think console three or four outputs anything that is going on, so maybe it had outputted the error...

Sorry for the not-so-direct solution/s, since, my signature states, i'm a noob, but i love to help.:)

---

### Post by Elmin on 2006-07-22
Hi Ziox,

I have tried the Ctrl Alt F7 and the Ctrl Alt Backspace but no, it doesnt solve the problem. The picture is still gibberish. When I do a sudo shutdown -r now, the screen was like in distorted 8 bit colour. I can see the Ubuntu word though barely recognizable and the process shutdown but else the colour is just out. 

I might be having some problem downloading the alternative cd. Is there no other choice that I can get from the Live CD that I have received ? Was wondering why the alternative is not included with the package that was ship in by the ShipIt....

@@ Elmin

---

### Post by Ziox on 2006-07-22
Apparently, Ubuntu is promoting the use of live CD, which is more (or less) user-friendly...as for other options, i'm going to try it myself. I'll post as soon as i get it to work.

Ok...i don't there is any none-gui options.  So let's see if xorg is at fault.  Go to the command line (virtual console #1) and type:

"nano /etc/X11/xorg.conf"

then go down to the section labeled "Device," below, it should i identify your graphic card and the driver it uses.  Can you copy/write that here?

---

### Post by Elmin on 2006-07-22
Hi again,

Section "Device"
Identifier " NVIDIA Corporation NV41.1 [GeForce 6800]"
Driver "nv"
BusID "PCI:1:0:0"
EndSection


This is what I got from the xorg.conf.



@@ Elmin

---

### Post by Ziox on 2006-07-22
alright i think i see the problem, change "nv" to "nvidia" and then restart X, ctrl + alt + backspace. If that doesn't work, then change "nv" to "vesa" and restart X again.

---

### Post by Ziox on 2006-07-22
did that do the trick?

---

### Post by Elmin on 2006-07-22
Hi Ziox,

Thanks for your tips on handling my problem. Yup, I can see the Live CD with "vesa" now. I read about this from the other post but it didnt strike me that I need to do the changes before booting up into the Live CD. Maybe gotten myself information overloaded way off.... 


Now am installing the clean copy into my HDD... Hopefully I didnt mess up my partition ... Ihihi :-D  Now, hopefully I dont have to do the step back when I restart my PC...

Thanks anyway and have a nice night...


@@ Elmin

---

### Post by Ziox on 2006-07-22
great...glad it works for you now.
if you run into anymore trouble...Post and they will come....

....as for a good night...it's always daytime in the US:)

---

