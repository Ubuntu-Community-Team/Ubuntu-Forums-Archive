---
title: "Feisty and low resolution"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by SierraKilo on 2007-04-26
Hi guys,
I'm trying to install feisty on my disk, but I encountered a problem. I seem to be unable to select any screen resolution higher than 800x600 which makes the installation impossible since all control buttons are 'below' my screen. In some other threads I read about reconfiguring the xorg.conf manually, which I guess is impossible in my case since I'm just booting from the livecd. So is downloading the restricted nvidia drivers since they ned a system restart to work. 
To my system: I'm running a Core2Dual, with a Nvidia Geforce 7950 from Asus and a 19' flat-screen from LG connected via DVI.

Hope someone can help me.
thanks!

---

### Post by lw5 on 2007-04-26
I guess you have several options you could try;

The first is to alter your boot procedure (F6?) and add 'vga=791' (this should set your resolution to 1024x768) to your bootline.
If you have onboard vga support on your motherboard, you could try to yank out your videocard and put it back after installing.

---

### Post by SierraKilo on 2007-04-26
nope, vga=791 didn't work and I don't have another VGA onboard :(

---

### Post by javierfh on 2007-04-30
> **SierraKilo said:**
> Hi guys,
I'm trying to install feisty on my disk, but I encountered a problem. I seem to be unable to select any screen resolution higher than 800x600 which makes the installation impossible since all control buttons are 'below' my screen. In some other threads I read about reconfiguring the xorg.conf manually, which I guess is impossible in my case since I'm just booting from the livecd. So is downloading the restricted nvidia drivers since they ned a system restart to work. 
To my system: I'm running a Core2Dual, with a Nvidia Geforce 7950 from Asus and a 19' flat-screen from LG connected via DVI.

Hope someone can help me.
thanks!

Hello,

i have tried yesterday to install feisty..and well i still have some problems with the nvidia drivers, but found some possible solution for my problem(...still have to try though). But your problem, seems familiar to me, or at least similar to what i went through yesterday.
When i finnished the installation, the max resolution i could get was 1024x ... or 800x600, cant remember now, but far from the optimal one. So what i did was to go to xorg.conf and add these new resolutions there , were the different resolutions are listed. 
I tried and didnt work, no matter what i tried, changing the driver name to vesa, nv, nvidia...but nothing changed, until i decided to take a look to it and decided to put the right refresh rates for my monitor...and believe it or not, it was just to add that and then it all worked. 

So i suggest you to go to the technicall specifications of your monitor and set the right vertical and horizontal refresh rates in the xorg.conf (and also add the right resolutions that in your case i assume that will be the 1280x ...)
just my two cents, please let me know if it works. If not, i could then take a look to your xorg.conf file.


Javi

---

### Post by FunnyLookinHat on 2007-05-16
I know this reply is a bit late but it should get you working...

When you boot up the LiveCD you need to select "Safe Graphics Mode" before you hit enter on the "Install Ubuntu" option at the boot menu for the CD.  This should allow you to get a decent resolution while installing ubuntu.

After you have installed, you should go to System - Administration - Restricted Drivers Manager and check the box on the nVidia line labeled "Enable".  You will have to restart your system for the changes to go into effect, but this should provide you all of the necessary resolutions for your screen and give you a better performance out of your graphics card as well.

Cheers,
David

---

