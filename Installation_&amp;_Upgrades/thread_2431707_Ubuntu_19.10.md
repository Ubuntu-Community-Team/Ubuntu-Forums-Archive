---
title: "Ubuntu 19.10"
date: 2019-11-20
forum: Installation &amp; Upgrades
---

### Post by gordie692 on 2019-11-20
Hope this is where it goes I got 19.10 to work and works great faster and snappy I turned off the UEFI and disabled it in bios and way it went so just a heads upo for anybody wanting to install this OS because my laptop is a Dell Inspiron 15 AMD with A9 7th processor running 8 gigs of ram thought secure boot would be okay but kept getting black screen after boot up

Also I'm thinking on this for my desktop when I get my new board I had enough with Windows 10 not a happy camper so this winter I'm going to get back into terminal work again

---

### Post by CelticWarrior on 2019-12-27
Disabling Secure Boot OK.
Installing in Legacy like you did, NOT OK.

This is just a reminder for users reading this in the future: **In any modern hardware always install in UEFI mode.**

---

### Post by oldfred on 2019-12-27
New systems really should be UEFI/gpt. 
But if ok with 35 year old BIOS in new system that is your choice.
At very minimum I would use gpt partitioning and include both a bios_grub for BIOS boot and an ESP for UEFI boot. Then you only have to reinstall grub to convert from BIOS to UEFI.

May be similar system, and back in 2017 has a few issues.
       Dell Inspiron 15 5567 AMDGPU-Pro driver causes a kernel panic  Jan 2017
[https://ubuntuforums.org/showthread.php?t=2347889](https://ubuntuforums.org/showthread.php?t=2347889)

---

