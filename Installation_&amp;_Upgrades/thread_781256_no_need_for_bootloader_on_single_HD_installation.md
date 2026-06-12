---
title: "no need for bootloader on single HD installation?"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by bergqvistjl on 2008-05-04
Hi, i am a fairly new ubuntu user and i am installing ubuntu onto a seperate hard drive (IDE) with wnXP on a SATA drive. My question/s is this:

If i disconnect my winXP sata drive and install ubuntu on the IDE drive, will ubuntu bother to install a bootloader menu, as it thinks there's only 1 OS (ubuntu) on the only HDD so there would be no need to choose an OS on startup? If that works, could i then plug back in my winxp drive and just use the bios to choose which hdd i want to load off?

---

### Post by HunterThomson on 2008-05-04
You still need grub to boot Ubuntu even if it is the only OS. But you only come to a menu screen of you press Esc or the down arrow key at bootup.

---

### Post by bergqvistjl on 2008-05-04
ok, tho can you not have the OS choices menu then?

---

### Post by bobnutfield on 2008-05-04
If I understand your question correctly, you intend to disconnect the appropriate drive whenever you want to choose between OS's?  That seems like an awfully necessary way to do things, but you would still need a bootloader on the driver where Ubuntu resides, whether it is Grub or syslinux (I have never used syslinux to boot my Linux OS's).  A simple grub installation on the MBR of your first drive will allow you choose your OS at boot up, eliminating the need to disconnect anything.  

If you are concerned about damaging your windows installation, you can restore the MBR at anytime with your installation cd for windows.

Bob

---

### Post by HunterThomson on 2008-05-04
> **bergqvistjl said:**
> ok, tho can you not have the OS choices menu then?

Ya you will not have one it will just count down from 3 and boot.

---

### Post by HunterThomson on 2008-05-04
> **bobnutfield said:**
> If I understand your question correctly, you intend to disconnect the appropriate drive whenever you want to choose between OS's?  That seems like an awfully necessary way to do things, but you would still need a bootloader on the driver where Ubuntu resides, whether it is Grub or syslinux (I have never used syslinux to boot my Linux OS's).  A simple grub installation on the MBR of your first drive will allow you choose your OS at boot up, eliminating the need to disconnect anything.  

If you are concerned about damaging your windows installation, you can restore the MBR at anytime with your installation cd for windows.

Bob

You could also install Super Grub form a Super Grub Live CD if you don't have the windows CD and wish to get rid of ubuntu. But why did you want to install Ubuntu like that anyway?

---

### Post by bergqvistjl on 2008-05-04
No, in my bios i can choose which hard drive to boot off, so when its all done, i want a bootlaoder on my linux disk which will boot straight into ubuntu, leaving my original windows bootloader on my windows disk intact, so if i want to boot into windows i just change a setting in the bios and it will boot off my windows HDD

---

### Post by bobnutfield on 2008-05-04
OK, you can do that.  Just be sure during the installation process that you install the bootloader to the partition (disk) you are installing Ubuntu to. Pay close attention to this because it will install to the MBR if you let it.

Bob

---

### Post by bergqvistjl on 2008-05-04
yh before, i had installed the mbr to my linux disk, told the bios to boot from my linux disk and it all worked fine, execpt grub gave me the message that it couldnt mount the partitions (none of them), but when i told the bios to boot from my windows drive, grub loaded and it booted fine, despite the fact that i told ubuntu to load the bootloader onto my linux disk. Weird

---

