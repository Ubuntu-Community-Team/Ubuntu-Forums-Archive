---
title: "MBR and GRUB problem ?"
date: 2011-12-05
forum: Installation &amp; Upgrades
---

### Post by willybernal on 2011-12-05
Hello, 

I deleted an ubuntu partition. Then had some problems with GRUB, so I fix Windows master Boot Record [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html). Now, I want to install ubuntu again in another partition, but the CD does not load, it boots from it, but stays in the first violet screen, the mouse still works, but nothing loads. I tried different distributions, CDs, USBs. I even tried wubi, but no success, same problem. I guess I have a problem with GRUB/MBR, not sure what to do or how to fix it. Any help appreciated. 

Thanks,

---

### Post by drs305 on 2011-12-05
Hi willybernal,

Welcome to the Ubuntu forums.

You may need to set a kernel option to get the CD to boot. Video problems are often solved by booting with the 'nomodeset' option. Power-related hang-ups may benefit from various apic options.

To add these options during a CD boot, press the F6 key as the CD starts. Pressing F6 again lets you choose some options or manually enter them. 

Here is a community doc that explains it:
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

---

### Post by willybernal on 2011-12-08
Hello, 

I tried the different advanced boot options under F6 key. However, this keeps giving me the same problem, it will try to load the cd but will only stay at a empty violet screen. Is there anything else I can try to diagnose the problem?

---

### Post by raja.genupula on 2011-12-09
[http://ubuntuforums.org/showthread.php?t=1475462](http://ubuntuforums.org/showthread.php?t=1475462)
[http://ubuntuforums.org/showthread.php?t=1468687&page=2](http://ubuntuforums.org/showthread.php?t=1468687&page=2)

---

### Post by willybernal on 2011-12-09
Setting nomodeset and including the following options xforcevesa no splash --
allowed me to install ubuntu. I was able to run the whole installation, when the system restart and choose the operating system to load (in GRUB) ubuntu does not load, it only gives me a black screen. My other OSs keeps working just fine.

---

### Post by oldfred on 2011-12-09
If you needed nomodeset on liveCD you definitely will need it on first boot. If then you install proprietary drivers like the nVidia driver then you will not need the nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
[COLOR=Red]On first boot after install[/COLOR], press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

