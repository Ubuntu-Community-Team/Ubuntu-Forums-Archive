---
title: "No way to install Ubuntu on my Toshiba Satellite A215"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by Joanna_Moreno on 2013-10-17
I've been trying to install Ubuntu for the last 3 days and  went through dozens of topics but nothing works for me, so I hope you can possibly help me here...


  My laptop model is Tohshiba Satellite A215. Few months ago I had Ubuntu  12.04 installed on this machine (from LiveCD, everything worked perfect) but then I had to format my hard drive  and install Windows 8. Since that time, no hardware nor BIOS version changed. So  now I want to install Ubuntu, to have it along with Windows. But every  time I run the installer some problems appear. Here is what I tried:

  
[LIST]
[*]starting installation normally -> gets me some strange lines  about Pnp Bios. The last line says "Pnp Bios version 1.0, entry 0xf000  :0x9afb, dseg 0x400" 
[*]starting installation with pnp bios=off -> the same 
[*]starting installation with nomodeset -> gets me black or gray screen (depending if I use CD or USB) 
[*]starting installation with nomodeset + acpi=off + noapic -> gets me blinking cursor 
[*]starting installation with pnp bios=off AND I delete quiet splash  -> WORKS. The files load, there are some fails, though there's no  time to note them down and finally the installation screen appears. I  choose a partition to install the system, click Next and AGAIN i get  black screen or black screen with a blinking cursor. 
[/LIST]
  
I also tried: 


[LIST]
[*]running different versions (12.04, 13.04) 
[*] running both from USB and CD 
[*]running from an alternate installer 
[/LIST]

In every case the same things happen. I would really appreciate any ideas...

---

### Post by oldfred on 2013-10-17
I have nVidia on desktop and Intel on my old Toshiba laptop, but for AMD one of these 3 may be better than nomodeset?

 

[LIST]
[*]Generic: xforcevesa or nouveau.modeset=0 
[*]Radeon: radeon.modeset=0 
[/LIST]

---

### Post by Joanna_Moreno on 2013-10-20
> **oldfred said:**
> 

[LIST]
[*]Generic: xforcevesa or nouveau.modeset=0 
[*]Radeon: radeon.modeset=0 
[/LIST]


Thank you Sir! Nobody could help me and then finally **pnpbios=off**+**xforcevesa** worked! Ubuntu has been installed properly.
The problem now is that every time I boot my laptop, Ubuntu won't boot untill I add these two parameters. It's not a big deal, I've edited a grub file with GRUB Customizer so I don't have to enter these every time I run my laptop. So my question is, should I be worried about it? The system works fine, but I'm not sure whether those parameters won't do any harm to my machine? Is it all safe??

---

### Post by oldfred on 2013-10-20
I think vesa is the lower level video driver that the liveCD uses.  Not sure what your pnpbios setting does.

Often with AMD you have to install drivers but I am not current on AMD. They obsoleted some older chips/boards and you then have to use a legacy driver.

---

