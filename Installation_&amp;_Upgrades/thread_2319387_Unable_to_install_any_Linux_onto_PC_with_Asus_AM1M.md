---
title: "Unable to install any Linux onto PC with Asus AM1M-A"
date: 2016-04-03
forum: Installation &amp; Upgrades
---

### Post by Jacob_Espinoza on 2016-04-03
I am unable to install any variant of Linux onto my custom built PC with an Asus AM1M-A motherboard, including the AMD 5350 APU.

The furthest I get along in the install process is with the Ubuntu 14 LTS (x64) Mini ISO burned to a CD. I get as far as "select and install software" before errors occur.
I have to manually specify the correct kernel or else the install fails at "installing base system." I use the linux-signed-4.4.0.... kernel.

The most obvious error is listed below:
```
Apr 3 22:10:19 kernel: [ 2552.730048] python3.4[12316]: segfault at 8030 ip 0000000000572934 sp 00007ffc91aa5480 error 6 in python3.4[400000+2fe000]
```
Which leads to
```
Apr 3 22:10:20 in-target: Errors were encountered while processing:
Apr 3 22:10:20 in-target:  dh-python
Apr 3 22:10:20 in-target:  python3.4-minimal
Apr 3 22:10:20 in-target:  python3.4
Apr 3 22:10:20 main-menu[275]: WARNING **: Configuring 'pkgsel' failed with error code 100
Apr 3 22:10:20 main-menu[275]: WARNING **: Menu item 'pkgsel' failed.
```

I have gone into the BIOS settings many times to modify options so I can avoid UEFI mode; Asus support was very unhelpful - simply saying they 'do not support Linux.'

I have tried, in total, almost 20 different distributions of Linux and they all fail installing. I would rather not have to go to Windows; however, I have a feeling that I may have to buy a new motherboard because the current one does not appear to have the right settings to be compatible with Linux.

I can post more information about the system configuration and errors.

Thanks

---

### Post by X-RED_Tech on 2016-04-03
Perhaps your problem is trying to avoid UEFI. Really, why?

---

### Post by rosswmcgee on 2016-04-03
How big is the hard drive?

---

### Post by Jacob_Espinoza on 2016-04-03
I am trying to avoid UEFI for compatibility reasons, frequently the BIOS will not boot into UEFI versions of installation media.

My hard drive is a 128 GB Transcend SSD.

---

### Post by him610 on 2016-04-03
I also own an Asus AM1I-A with AMD Athlon 5350 APU which I built last year. Ubuntu 14.04 (full ISO version) was successfully installed on it after I completed assembly. At the time, I thought I had installed it with UEFI disabled; however, I was mistaken. 
A major disadvantage is its use of Secure Boot. Normal Grub commands can not be used from the Grub command line; other than that, I have encountered no problems with the installation.

---

### Post by Jacob_Espinoza on 2016-04-07
How did you install that version? Also your motherboard model is different that mine. Can anyone offer any troubleshooting tips? Really, no version of Linux wants to install on my machine.

---

### Post by gordintoronto on 2016-04-08
Have you tried the beta 16.04, perhaps the Xubuntu version? That motherboard is newer than 14.04, which often causes problems.

"I have to manually specify the correct kernel or else the install fails at "installing base system." I use the linux-signed-4.4.0.... kernel."

I (successfully) test about a dozen Linux distros or versions a year, and I've never tried to use a kernel which was not part of the distro.

---

### Post by Akimoge on 2016-04-08
Try 15.10 or new 16.04. I had same problem with my UEFI motherboard and this fixed my problem. 
BTW: did you tried Legacy BIOS and MBR partition table?

---

### Post by oldfred on 2016-04-08
I have an Asus mother board for Intel, Z97-ar. But I had to make a lot of changes to UEFI settings.
I would expect even though yours is AMD, many settings would be the same.

And if I remember correctly the UEFI secure boot setting was really "Windows" meaning Secure boot or "Other" meaning not secure boot. And Windows 7 does not support secure boot, so it also needs "Other". So much for supporting Windows, Asus.

To get UEFI to consistently work I turned off Secure boot and had to turn on USB boot, and UEFI only boot. Even UEFI and CSM/BIOS would not let me boot consistently in UEFI mode.

---

### Post by Jacob_Espinoza on 2016-04-09
I have downloaded and burned those two versions to a disc. I returned the RAM because it wasn't on the vendor qualified list, so I can't use the system until next week when the new RAM arrives. I'll update you all then...

---

### Post by P-I H on 2016-04-09
I am using that motherboard in two systems. One is Ubuntu Server 14.04 and one Kodibuntu 14.04. I will upload some pictures of my bios settings Sunday or Monday.

---

### Post by him610 on 2016-04-09
> How did you install that version?

I installed Ubuntu from a DVD with LTS 14.04 that I had used before.  It has been awhile now, but I can recall no issues during installation. 

> your motherboard model is different that mine

True. When one character is changed in a model designator, it normally means one is a later model (I precedes M), or possibly, an update to the mainboard firmware; however, [COLOR="#FF0000"]they are both basically the same.[/COLOR] Not completely true - I have determined your AM1M-A is microATX while my AM1I-A is mini-itx. I guess that accounts for the ***M*** in yours and the ***I*** in mine.

Don't like secure boot. When one goes from grub menu into the grub terminal, none of the normal grub commands are allowed, not even "help"

---

### Post by P-I H on 2016-04-12
These are my bios settings

---

### Post by oldfred on 2016-04-13
What are Secure boot settings?

And with my Asus, I had to use UEFI only, not UEFI & CSM to get flash drive or system to boot in UEFI mode.

---

### Post by Jacob_Espinoza on 2016-04-16
I finally got it working, thanks oldfred. I had to change the secure boot settings to force UEFI and then I had to use a USB flash drive instead of a DVD. It is quite unfortunate how Asus will not allow the complete disabling of secure boot.
But thanks once again!

---

