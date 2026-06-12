---
title: "can't install ubuntu on my computer"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by gufide on 2011-02-19
Hi there, I trying to re-install ubuntu on my computer. I'm currently on 10.10 (upgraded from 10.04) but live cd doesn't work with my hardware! I'm on asus G60Jx laptop with nvidia gts 360m. I'm not the only one to have this problem. It's my third message on this forum about this because no one answering me after 5 bump. I ask for help in ask ubuntu. I got "install ubuntu 10.04 and upgrade it, it don't take so much time" ok, I'll do that, but for 11.04, can I expect to be able to use the liveCD installation or I will install 10.04 to upgrade it after? I know that I can't change nothing for 10.10 but a bug is bug, and I wish that my computer will be more supported, thank to all. And this time, answering to me please and show me how can I report this. I know that I can use ubuntu-bug but I didn't found the fine section. Thank

---

### Post by gufide on 2011-02-20
55 view 0 replies...

---

### Post by PaulReaver on 2011-02-20
have you tried making a live usb??? that's what i do.... works quite well. :)

---

### Post by gufide on 2011-02-20
I will try this, I hope this is only that :P
I'll be back...

---

### Post by gufide on 2011-02-20
No, it didn't solve the problem. This is a huge graphical glitch, I got a black and white screen when X start, and I'm not the only one; every person with the asus g60Jx got this problem. I see that if I restart the computer and I boot with the live cd, I see part of the last image I got of my current desktop! It can be a problem with the graphic memory...

---

### Post by nhtrader on 2011-02-20
I have the same problem. It's driving me crazy.

1. I created a LiveCD (downloaded Mythbuntu 10.10 32bit) - > Fails.
       btw, the first logo screen is ok. The second logo is ok. Then scrambled display.
2. I created a LiveCD (downloaded Mythbuntu 10.10 64bit) - > Fails. Same problem
3. I created a LiveCD (downloaded Xbuntu 10.10 32bit) - > Fails. Same problem
4. Created USB custom LiveCD Mythbuntu 10.10 with many upgrades but no proprietary drivers (no ATI/AMD, no Nvidia) - only open source drivers. -> Fails. Same problem.

I've been hacking away at this for the past two weeks. No luck yet with Asus G60JX. However, note that all other PCs I own work fine with USB LiveCD or plain old LiveCDs. 

That includes Desktops:
      1. Intel Q8200 CPU with Intel G45/G43 Express chipset
      2. AMD X2 245 2.9Ghz with AMD graphics chipset
      3. AMD sempron3000 with Nvidia Graphics Card

Successful Laptops:
      1. AMD Turion X2 RM-70 CPU with ATI Radeon HD3000 Graphics
      2. AMD Athlon XP-M 3000 with Nvidia Geforce 4 420 Go

Failed Laptop:
     Asus G60JX  Intel i5 with Nvidia Geforce GTS360M with 1Gb VRAM

---

### Post by jerenept on 2011-02-20
What version of Intel i5? It may be a SOC (System-on-chip) processor, in which case there may be confusion about which graphics system it's going to use- the GTS380 or the i5's builtin graphics card. The new Sandy Bridge chips use this technology, unsure about the older Nehalem's

---

### Post by nhtrader on 2011-02-20
> **jerenept said:**
> What version of Intel i5? It may be a SOC (System-on-chip) processor, in which case there may be confusion about which graphics system it's going to use- the GTS380 or the i5's builtin graphics card. The new Sandy Bridge chips use this technology, unsure about the older Nehalem's

This is all I know:
CPU i5 M430
NVIDIA® GeForce® GTS 360M, with 1GB GDDR5 VRAM


In the mean time, I got past the scrambled screen. Hurray! I read another thread which suggested trying boot option "nomodeset". However, being a newbie, I don't know how to use this information. 

So I learned how to modify the options b4 continuing with the trial install.

With custom Live CD...
 I needed to press <TAB> 
 then delete the last two characters "--"
 type: nomodeset --<E> 
      (note this needs a leading space from other text visible)
      (ex: quiet splash nomodeset --)

Successful boot/startup!

With the standard download Xbuntu 10.10...

When Xbuntu Menu Appears (to select install or trial)...
  press F6
  scroll down list and put an x infront of nomodeset
  select trial use
  xbuntu appears. hurray!


Using the nomodeset option cured the scrambled screen, but it also restricts the number of display resolutions that are available. I only have two resolutions available: 800x600, and 640x480. But the good news is that I can use whatever flavor of ubuntu I want.

Also, worth mentioning is that I saw this error msg:
    failed to get i915 symbols:  turbo graphics disabled
but the trial-install pushed past this (with the nomodeset option) and the LiveCD completed the installation.

---

### Post by gufide on 2011-02-21
> **nhtrader said:**
> Also, worth mentioning is that I saw this error msg:
    failed to get i915 symbols:  turbo graphics disabled

me too, I got this on boot with 10.10 (upgraded from 10.04)

---

### Post by gufide on 2011-02-21
I really hope that this bug will be solved on 11.04

---

### Post by giangqaz on 2011-04-07
me too.
i'm using asus laptop (x82s) with graphic card hd 3xxx 
i can't install ubuntu 10.10 from CD or USB ( black screen with blind cursor ) . And the same problem happened with 11.04beta1 (only black screen).:confused::confused:

---

