---
title: "Ubuntu 16.04.2 is not installed on ASRock H110M"
date: 2017-06-28
forum: Installation &amp; Upgrades
---

### Post by lady3mlnm on 2017-06-28
Hi!
Sorry for my English. I'm new in Linux and try to pass to Ubuntu, but can't install it. I tried different methods (via USB flash drive, via DVD-drive and via Wubi), but the installation process always froze soon after beginning. I captured to my phone 2 of my attempts (via DVD-drive and via USB flash drive). I even wait for half-hour, but there's not further progress.

[https://youtu.be/e4IVHa6dQZw](https://youtu.be/e4IVHa6dQZw)

Sometimes installation process occurs little differently. This is photo of errors that sometimes pop up at the beginning. I don't know where I would can find installation log.

[IMG]http://bhlady.narod.ru/resources_outer/Ubuntu-error-1.png[/IMG]

Sometimes I even reach selection menu:

[IMG]http://bhlady.narod.ru/resources_outer/Ubuntu-error-2.jpg[/IMG]

I even can't launch Ubuntu in trial mode. I tried all options in the menu (including UEFI). Self-check is OK. The attempt to launch Ubuntu 17.04 gave the same behavior.

I'm new in Linux but experienced user in Windows. I have active assistant via internet from several people who knows Linux but we can't solve this problem. Google don't help.

I would like to indicate that my motherboard ASRock H110M-DGS don't support installation Windows XP and has difficulties at installation Windows 7. User must impose special patch on installation image to begin process: [http://www.asrock.com/microsite/win7install/](http://www.asrock.com/microsite/win7install/) .

The configuration of my PC:
motherboard: ASRock H110M-DGS
hard drive: SSD SmartBuy Splash 240 GB
CPU: Intel Core i3-6100 Skylake
RAM: Samsung DDR4 2133 DIMM 8Gb x2
videocard: GIGABYTE GeForce 8800 GTX
audiocard: Creative Sound Blaster Z

I hope that I receive help and will be able to install Ubuntu.

---

### Post by johndough2 on 2017-06-29
Hi

Perhaps you could try a small light linux to prove the system. For instance Slitaz runs in ram and does not need to install, if you can create a working cd/usb with slitaz on this will be a big step. MultiBoot USB or LinuxLive USB Creator

The link you posted suggests DVD install will work easier than USB as "Enhanced Host Controller Interface, so you might  find it difficult to install your Windows 7 operating system since the  USB ports won't work".

Then your ubuntu problems will be in the area of the HDD or BIOS setting I think, and we can tackle those later.

TinyCore, Slitaz, Lubuntu, LXLE, DSL, Puppy or Linux Lite.   Some of which are Ubuntu based.

[http://www.techradar.com/news/10-of-the-best-lightweight-linux-distros](http://www.techradar.com/news/10-of-the-best-lightweight-linux-distros)

---

### Post by oldfred on 2017-06-29
That system can easily run full Ubuntu.
Issue probably is nVidia card.
Install & first boot often need nomodeset boot parameter added until proprietary driver from Ubuntu repository added.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Your nVidia card is older, you may have almost same performance from Intel video. And that should install without boot parameters. Just move video connector to motherboard.
But with my system I made a mistake on selecting motherboard. It had HDMI & Displayport out, but old monitor only had DVI and vga in. So I also use a some what older nVidia card.

Your nVidia is older, so be sure to install correct driver. And only install from Ubuntu repository not from nVidia.  Nvidia freezes drivers for older cards that then do not support all the new features in a newer card & driver. So you may need the older driver.
      
 nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

### Post by lady3mlnm on 2017-06-29
Yes! I was wrong. The real problem was in my outdated videocard. I'm too tired today to finish but necessarily test all tomorrow and write here.

---

### Post by lady3mlnm on 2017-06-30
**oldfred**, thank you very much! This words I already write from Ubuntu!

The problem was not in my motherboard, but in my videocard. I need this videocard because I have 2 monitors. Moving connector from monitor to motherboard did not work, so I fully deleted videocard out of my system. After that Ubuntu installed without problems.

After inserting videocard back Ubuntu, that was already installed, again refuse to boot, show back screen. No matter, where the monitor was connected. I again pull out videocard, installed drivers for it and reboot with videocard - and after that was able to use both my monitors. (I use drivers nvidia-340, from repository - I hope that made this write, I never done such things before.)

Unfortunately this is not full victory. When I tried to mutually align desktop there were numerous freezings and black screens. I achieved the desired results, but I don't like such behavior. I know that in such cases it is recommended to install older drivers. Or it can be better to buy new videocard than solve such problems. But this is already another problem. :-)


> **johndough2 said:**
> 
Perhaps you could try a small light linux to prove the system. For instance Slitaz runs in ram and does not need to installI've checked (before described above actions). Slitaz work well, even with my old videocard without any additional drivers.

---

### Post by oldfred on 2017-06-30
With your card, only the 340.xx version is recommended as per nVidia legacy driver link above.

I have nVidia 620Gt and just use the open source driver. One of my installs on this system I did use the nVidia driver and did not notice any real difference. But I only have one monitor.

I thought nVidia supported up to 3 monitors. 
There was an issue where nVidia supported 4 monitors in Linux but only 3 in Windows, so Microsoft said contract prevented nVidia from having more features in any other version than Windows, so they had to change it to 3 for Linux drivers. This was several years ago, do not know most current info.

---

