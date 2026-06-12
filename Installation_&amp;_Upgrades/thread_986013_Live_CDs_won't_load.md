---
title: "Live CDs won't load"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by dkaddict on 2008-11-18
I am having problems trying to get any Ubuntu Live CD after Feisty to load on my machine so I can upgrade. At the moment I am stuck with Feisty. I think it may be something to do with my video driver. I have Via onboard graphics and always used the Openchrome driver but switched to the proper Via one when I found out they had written one. The Feisty live CD loads fine but anything after just won't have it. I either get the black screen with the desktop running or if I try to boot into Safe graphics mode, the load process gets hung up and I have to shut down. I have tried the Gutsy and Hardy alternative CDs with no success either. Can anyone help? I need to get the CD to load the VESA driver from boot I think. That is how the previous CDs worked but these seem to be having trouble. Would I be better off trying to load a Gutsy Live CD if I put my xorg.conf back to VESA before I try it? I know that the Via script changed quite a bit and don't see how the live cd would deal with it?

I really could do with upgrading but my machine can't handle the upgrade, it cuts out half way through every time and I end up with a fresh Feisty. I have to do it from CD. Please help us out!

Cheers

---

### Post by mikewhatever on 2008-11-18
Are you talking about upgrading or reinstalling? The reason I ask is simple, upgrading is usually done from Alternate cds, as mentioned in [UPGRADING INSTRUCTIONS]("http://www.ubuntu.com/getubuntu/upgrading"). I'm sure you'd looked at them, right?

---

### Post by dkaddict on 2008-11-19
Mikewhatever; cheers for getting back to us yeah.

I have to do a fresh install because my laptop crashes half-way through the upgrade process. It (the notebook) is getting old and tired and will crash if I leave a web page with loads of Java loaded for too long so the upgrade is just too much for it to handle. I think the processor gets too hot or something? I can't get a new machine so have to stick with this one for a while. I know it can handle a fresh install because I have had so many crashed upgrade attempts.

Ok, this is an edit from now on as I think I have found the problem. I ditched the official Via driver and compiled and installed the Openchrome one so I can switch between Via and Vesa without having to mess about with my xorg.conf so much. I switched to the Vesa driver and tried a Kubuntu 7.10 live cd in safe graphics mode. It nearly loaded. KDM was loading but crashed. I had never made it this far and the error message I got was about my machine not supporting CPU Frequency Scaling and the live cd being unable to create the associated file for CPU Freq Scaling. So, I need to be able to turn off that somehow? Can I use a cheat code like noapic or something like that? To get USB and wireless to work I had to edit the /boot/grub/menu.lst and add 'irqpoll', is there something like that which will stop the live cd from wanting to create the CPU frequency scaling file so KDM or Gnome will load?

Sorry about all of the probably dumb Questions. I will go and see if I can find out and will post back ASAP if I can find out anything!

Give thanks for your time and any other answers

JahGuide

---

### Post by mikewhatever on 2008-11-19
I am no expert with cheat codes (boot options), but noapic seems like worth trying, along with several others, according to the link below.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

