---
title: "Trouble installing 12.04 on a new system"
date: 2012-11-08
forum: Installation &amp; Upgrades
---

### Post by neonathon on 2012-11-08
Hello Ubuntu community

I seem to be having some issues installing Ubuntu 12.04.1 64 bit on a new system I built. The cd I burned sometimes allows me to get to the installation phase, but the installation never works. However, most of the time I get stuck on the loading screen. It gives me a few different errors each time I try, most often "TCO timer mmio address "random text" already in use. I'm running this on an AMD FX 1850 processor with an ASUS saber tooth mother board, evga GeForce 660ti graphics card, lg bluray rw drive, and a seat ate 3tb hard drive. I've burned multiple CDs and tried many times, but cannot get a stable installation. Help would be greatly appreciated. Thanks

---

### Post by Mr_JMM on 2012-11-09
Sorry, just to get the obvious questions out of the way...

Have you been confirming the md5sums of the downloaded ISO and of the completed DVD?

---

### Post by varunendra on 2012-11-10
> **Mr_JMM said:**
> Have you been confirming the md5sums of the downloaded ISO and of the completed DVD?
+1
How To MD5Sum : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by 2F4U on 2012-11-10
Can you verify if this bug report is similar to your problem?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1055096](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1055096)

---

### Post by oldfred on 2012-11-11
Is this a UEFI system? You have to use 64bit version.

And with a 3TB drive you have to use gpt partitioning. If you are thinking of installing Windows you have to have an UEFI system as Windows only boots from gpt with UEFI. If you use MBR you drive will only be 2.2TB not 3TB.

With Ubuntu and gpt you need a bios_grub partition if not booting in UEFI or an efi partition if booting in UEFI. And It works best with a small system  partition (25GB) and large /home, other data partitions or whatever you want rest of drive for.

With nVidia you need nomodeset on liveCD boot and then on first boot if proprietary drivers are not installed as part of install. Some systems also need other boot parameters. 

Some BIOS also need other settings. If you have fastboot or quickboot or something similar turn that off. 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Lots of technical detail:
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

