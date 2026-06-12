---
title: "Installation of Ubuntu 16.04 Hangs At Beginning"
date: 2016-09-01
forum: Installation &amp; Upgrades
---

### Post by chrisrhodes on 2016-09-01
After selecting the option to Install Ubuntu, I get a blank white screen with a blinking cursor at the top left.  If I edit the Install option to remove the quiet flag, I can see that it hangs after the initrd.lz line finishes.

[U]Things I Have Tried
[/U]Adding the nomodeset flag.
Adding the xforcevesa flag.
Removing all hard drives.
Running the option to verify the live USB data (still hangs).
Booting with UEFI instead (goes straight to a GRUB prompt).
Installing Mint 18 instead.
Installing CentOS 7 instead.

_Hardware_
CPU: A8-7600 (Has an integrated R7 GPU)
MB: AsRock A68M-ITX
SSD:  Corsair Force LE

Any ideas?

---

### Post by Bucky Ball on 2016-09-01
Welcome. Are you attempting to dual-boot with Windows or this is a Ubuntu-only install on an empty, unpartitioned drive?

---

### Post by chrisrhodes on 2016-09-01
Ubuntu-only, and the drive is brand new.

---

### Post by yancek on 2016-09-01
Did you verify the download of the iso file by running an md5 checksum?  Or can you try booting the DVD or flash drive in another computer to see if it boots?

---

### Post by Bucky Ball on 2016-09-01
Ok. Boot the install media (the Ubuntu installer, USB or disk) and when you get to the options, don't choose install, choose 'Try Ubuntu'. That should get you to a desktop. Once there, launch Gparted and you will see the drive as 'unallocated' and probably with an exclaimation mark next to it. Highlight the unallocated space and then 'Devices> Create partition table'. Close Gparted and reboot.

Now try installing. Might not work but worth a try.

---

### Post by chrisrhodes on 2016-09-01
> Or can you try booting the DVD or flash drive in another computer to see if it boots?

This was the key! Long story short:  

Universal-USB-Installer = *Bad*
Rufus = *Good*

I don't know what UUI was doing to my USBs, but that explains why no USB I created of any distro was bootable in any computer. :P

---

