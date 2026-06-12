---
title: "Boot and wireless problems"
date: 2016-08-27
forum: Installation &amp; Upgrades
---

### Post by juducky on 2016-08-27
OK. So I built my own desktop (asrock z710 k+ motherboard with 6th gen skylake i5) and evertime I try and install linux it fails when writing the grub boot code (I tried ubuntu desktop, lubuntu and mint). I found one of my old laptops and all 3 install fine on there. When I exchange the hard drive to my desktop it boots maybe every 4 time intermittently freezing my system, but no matter what I can't get wifi. The forum I found on installing my n1200 net gear usb wifi adapter led me to find that my sudo password is somehow different from that of my login so now I'm here. Any suggestions would be hugely helpful.

---

### Post by grahammechanical on 2016-08-27
And what specifically is the problem you want help with? Installing Linux and installing the Grub boot loader? Or setting up WiFi?

> The forum I found on installing my n1200 net gear usb wifi adapter led  me to find that my sudo password is somehow different from that of my  login so now I'm here.

More likely that the password needed to authenticate a connection to the router is not the same password as we use to login to Ubuntu. The password you need is also called a wireless passphrase; wireless key or WPA-PSK key. It is often a 10 character long combination of numbers & letters with all the letters capitalised.

---

### Post by juducky on 2016-08-27
Basically do you think it's my hardware that isn't compatible with linux? Or is there just something wrong with my coding?

---

### Post by oldfred on 2016-08-27
It it really a Z170?

Asrock has Asmedia ports on older motherboards, you cannot use any of those ports even for a DVD player without having issues.

I have a Gigabyte Z170 and after changing several UEFI settings to UEFI boot and partitioning with gpt, it has worked just fine.

Are you over clocking System?
  Asrock Z97 w/Core i7 5775C tried the "CPU OC Fixed Mode" of the ASRock UEFI setup.
[http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode](http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode)

What video card are you using or just the Intel internal one?

---

### Post by juducky on 2016-08-27
Yes I just built it this past December and I'm thinking it might be that my hardware is too new. I do have an internal cd/DVD writer/reader plugged in so I'll try installing without it if you think that will help. I'm just using the graphics card in the processor. What settings did you change in uefi?

---

### Post by oldfred on 2016-08-27
It is not whether you have DVD plugged in or not, but which ports on motherboard. Use only Intel.
Somewhere in Manual it should say if all are Intel or some are Asmedia. Not sure with your newer Z170 if it has those or not.

With my motherboards which are not Asrock. I turned off Secure boot which was called "Windows" or "Other", turned on allow USB and boot from USB ports, made sure CSM/Legacy/BIOS was off ( but some have posted with some systems that they have to have CSM on, but still can and must boot in UEFI mode). I also turned off fast boot or use normal boot in UEFI, turned off network boot as I will not use it, and did not want it looking for that. 
I have to save a list or take photos of BIOS as every new BIOS update resets to defaults. My new UEFI Z170, both gave a list of changes at end & allowed screenshots.

I also made sure I had newest UEFI from vendor.

What version of Ubuntu? You need 16.04, not 14.04 to have new enough kernel & support software for Skylake system.

[SOLVED] GPU Passthrough - IOMMU not working for me - on SkyLake 16.04 AsRock
[https://ubuntuforums.org/showthread.php?t=2322179](https://ubuntuforums.org/showthread.php?t=2322179)

---

