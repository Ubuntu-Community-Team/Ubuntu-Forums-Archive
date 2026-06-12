---
title: "Reboot Loop"
date: 2017-04-23
forum: Installation &amp; Upgrades
---

### Post by ragnarr023 on 2017-04-23
Stuck on this, and not usually one for forums but I'm a bit pooped. I'm trying to install Ubuntu 16.04 on my laptop. 

Laptop special are:
MSI GX60
Quad 2.5GHz (AMD a10-5750m)
Radeon card, struggling to remember, think it's in the 7xxx series.
16GB RAM

1TB HDD (with 400GB free) 
Win 8.1 (yuck) x64

I have installed Ubuntu countless times on my older laptop, and my laptop with windows 10, so I'm aware of the UEFI implications and the BIOS/CRM set up with Legacy mode on and secure boot off. 

I burned my ISO with Rufus with the UEFI format for gpt drives. Worked with my other ones. 

Can see the flash drive, can boot to it, and it brings the initial screen where it shows "install Ubuntu, test media, etc" (the initial black screen with the writing). 

The moment I choose install Ubuntu, the installer goes to the next screen where it is going to initialise, and then the laptop restarts and goes back to the install Ubuntu screen again. So basically, it crashes before it gets to the GUI installer. 

Can anyone assist me in this regard, or point me in the right direction. I miss Ubuntu, and don't want to get another laptop based on my own lack or fault finding.

---

### Post by deadflowr on 2017-04-23
Did you try running the Check disk for defects option in the menu?
I think that option should be available...

---

### Post by ragnarr023 on 2017-04-23
Pressed there, and it looped again. It seems it matters not what I choose, it loops.

If I press OEM install it goes to [ssd] assuming write through (or something like that) and loops right back.

---

### Post by ragnarr023 on 2017-04-23
Finally got this to show after some fiddling in the bios. 

Suppose it's a point to initiate diagnosis. 
[https://unsee.cc/pogamidu/](https://unsee.cc/pogamidu/)

---

