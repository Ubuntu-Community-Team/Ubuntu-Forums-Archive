---
title: "Painful experience of installing ubuntu on windows 8.1"
date: 2014-02-18
forum: Installation &amp; Upgrades
---

### Post by risk_junk on 2014-02-18
It took me almost 4 days to install ubuntu 13.10 on my current system and i got desperate once and once again. As a freshman to linux, I tried all i could to solve the problems i met, but i still find myself made it through luck for there is still much confusion. I hope my experience is helpful to others and i would be appreciate if someone could help me resolve my confusion.

My laptop is thinkpad x240, bought four months ago. 

At first i allocated enough free space (60g) and tried to install via wubi as most people do. But i failed at the beginning--cannot boot to ubuntu. I searched for solution, chose a seemingly [reliable one]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported")(the problem i met is exactly same as this one) and followed every step in it. I **turned off the secure boot**,  but i didn't have my problem fixed.
[IMG]http://i121.photobucket.com/albums/o211/akye23/IMG_2553_zpse8e4240e.jpg[/IMG]

[IMG]http://i121.photobucket.com/albums/o211/akye23/IMG_2568_zpsb722db50.jpg[/IMG]

Then guided by several related posts, i tried by easyBCD. I determined the information about my disk and each partition by DiskGenius, and configured NeoGrub bootloader as follow:
```
title Install Ubuntu

root (hd0,3)

kernel /vmlinuz.efi boot=casper iso-scan/filename=/ubuntu-13.10-desktop-amd64.iso quiet splash ro locale=zh_CN.UTF-8 noprompt --

initrd /initrd.lz
```
Still, failed to boot. I had restarted at least 50 times already.
[IMG]http://i121.photobucket.com/albums/o211/akye23/IMG_2572_zpsec130004.jpg[/IMG]
The next way i tried is booting from USB. I followed suggestions on the Internet too. I made a boot disk of ubuntu using UltraISO and restarted from USB. This time the result on the screen changed:
```
Start booting from USB device...

SYSLINUX 4.05 EDD 2011-12-09 Copyright (C) 1994-2011 N. Peter Anvin et al
```
But it just kept on displaying this information and the booting never succeeded though i  tried miany times again. I gave it up at that night and **turned the secure boot on(UEFI only)**, preparing to get back to normal life with win8. But accidentally I tried once more, and booted successfully from USB. The second stage began.

The installing process was not quite smooth. It stucked twice, one on the beginning, one on the end(about 90% completed). When i decoded to try the third time and restarted the laptop, grub appeared automatically and indicated that the ubuntu had been installed on the computer. I select the first option <strong>ubuntu</strong> but only got the error information:
[IMG]http://i121.photobucket.com/albums/o211/akye23/IMG_2579_zps9122415f.jpg[/IMG]
 So i tried to boot from USB again, but this time nothing but endless darkness was shown on the screen....By the way, any choice in the grub menu leads to an error or darkness on the screen, i have to exit from grub and use the BIOS to boot from other devices.This time i really didn't know what to do next, my friends told me to delete the incomplete system and restore the USB booting guide, but that's really troublesome. I was tired.

Guess what, I booted from USB successfully by doing nothing but **turning off secure boot** again, and the install began...Here by choosing "Reintall the system" i got stucked iin the middle once again, only by selecting "Something Else" and config the partition manually(i had to format each partition for there was something in it) did i finished.
[IMG]http://i121.photobucket.com/albums/o211/akye23/IMG_2583_zpsea7df41c.jpg[/IMG]

At that time i was to tired to celebrate, and I am still confused for many things:
Why wubi and easyBCD not work whatever secure boot is open or not?
Why USB booting was onlyl avaliable at UEFI first but can only be accessed when secure boot is closed afterwards?
And why the installing process often get stucked?

---

### Post by Bucky Ball on 2014-02-18
Yes, you finished. Press 'restart now' and make sure you boot from the hard drive and not the USB. The first line of the message in the last pic clearly states 'Installation has finished'. 

Please attach large pics by using the paper clip icon rather than inserting them in the body of your post. Spare a thought for those with slow connections and vision issues. The majority of your post is massive images with a bit of information in between. Some won't bother.

Incidentally, virtually no one uses Wubi (at least here), there's little support for it, and it is discontinued in newer releases.

---

### Post by fdrake on 2014-02-18
i ma not sure why you got the wubi problem, but if you turn off UEFI you will not be able to boot back into win 8.

Also we did not know how your hard drive was partitioned . It si hard to say wat went wrong. Coud have been an USB iso corruption, video card issue, etc.. it is hard to say since you have tried many thing

---

### Post by risk_junk on 2014-02-18
Thanks for your advice, i inserted these pics to help describe the problem i met because i am not good at using english...

The latest version 13.10 still uses wubi and many people talk about it so i tried it first.

---

### Post by risk_junk on 2014-02-18
yes there are many possibilities but problems came out initially.

i didn't turn off UEFI but secure boot so that both UEFI and Legacy are supported.

---

### Post by mastablasta on 2014-02-19
mistake no.1 is wubi.  
- wubi is not supported anymore. 
- i believe part of the reaosn why it is not uspported is that it doens't work on windows 8

wubi installs inside windows in a folder it cretaes a virtual drive. forget about wubi. it doesn't work. evcen when it did work it couldn't use 60GB space i believe. it had it's limitations. it was a fun way to try the os, but was a bit messy sometimes.

UEFI & secureboot are there to ocnfuse. well UEFI replaces BIOS, but secrueboot seems to be made to prevent users form installing anything else but MS windows. well later on Ubutnu got/created keys so they can also use the feature.

and so this page was made to guide the users: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

furthermore installing linux on it's own is a lot less complex than creating dualboot. which is not easy for beginners even on windows 7 laptops thanks to OEMs creating too many primary partitions while using MBR formating.

---

### Post by oldfred on 2014-02-19
Wubi does not work on gpt partitioned drives which all pre-installed Windows 8 systems have to have for UEFI boot.

EasyBCD is not required with UEFI boot and may complicate things. 
Some with BIOS Windows boot preferred it, but grub usually was better as a multi-boot manager. Grub2 is both a boot manager to manage more than one system, and boot loader. 
Windows is not designed to multi-boot anything besides Windows, but EasyBCD adds grub4dos and forcing grub2 into a partition to make it work.

UEFI is also a boot manager that lets you choose different systems to boot.

May be best to see details.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Do not say yes to 'buggy' UEFI until confirmed that you only can boot Windows, and that Ubuntu boot issue is caused by the buggy UEFI.

---

### Post by grahammechanical on 2014-02-19
I am not a freshman in Ubuntu but I would expect lots of difficulties when installing Ubuntu onto a Windows 8 machine. And quite a few with a Windows 7 machine. Which is why I will not purchase such things. I base my assessment on the posts I see in this forum. I do not blame Grub/Linux/Ubuntu developers for this. If it was not for their hard work in overcoming the obstacles we would only be running Gnu/Linux on older hardware. Such as the hardware that I am presently using.

Another area of frustration is video drivers. And that is a problem that goes back to the failure of the graphic adapter makers to be quick about releasing Linux video drivers.

---

### Post by jdeca57 on 2014-02-19
> **grahammechanical said:**
> I am not a freshman in Ubuntu but I would expect lots of difficulties when installing Ubuntu onto a Windows 8 machine. And quite a few with a Windows 7 machine. Which is why I will not purchase such things. I base my assessment on the posts I see in this forum. I do not blame Grub/Linux/Ubuntu developers for this. If it was not for their hard work in overcoming the obstacles we would only be running Gnu/Linux on older hardware. Such as the hardware that I am presently using.

Another area of frustration is video drivers. And that is a problem that goes back to the failure of the graphic adapter makers to be quick about releasing Linux video drivers.

I bought an W8.1 made by an OEM this year. No UEFI, no GPT. And absolutely no problems to dual-boot. What the developers have done is nothing less than outstanding. Linux works. Sure, your point of video (and other hardware) drivers is correct. But the main problem is the insertion of not only gpt but also uefi. It's not insurmountable, and later on everybody will get to know it, but it's an hindrance...

---

