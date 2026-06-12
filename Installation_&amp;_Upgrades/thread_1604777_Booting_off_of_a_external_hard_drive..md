---
title: "Booting off of a external hard drive."
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by Jetso on 2010-10-24
I am interested in buying a external hard drive, and booting several different OS's off of it. I already have Ubuntu 10.10, but I want other Linux distributions. I was wondering how to install the OS's on the external hard drive, instead of my laptop hard drive. Also what is the recommended/ most cost efficient hard rive I can purchase, and for how much $$$?

---

### Post by Fafler on 2010-10-24
It's possible to install most Linux distributions directly to USB drives these days. Or you could shrink your current filesystem and install multiple distributions side by side. Or you could install VirtualBox and install them inside a virtual machine (my preferred choice).

---

### Post by oldfred on 2010-10-24
Install to an external is not really different than install to a second hard drive. If USB, just recognize the the USB port will be somewhat slower than a SATA port, but most things work reasonably well. Just make as many 20GB / (root) partitions as you want. Do not share /home but put all data in a separate /data partition that you can mount in all installs.

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

Be sure to install a boot loader to the external so you can boot it separately and do not let any installs write their boot loader into the MBR of you internal drive. With Ubuntu you have to use manual install and manual partitioning to let you choose where to install grub2.
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by C.S.Cameron on 2010-10-24
If you are just looking for multiple Live installs check out:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by Jetso on 2010-10-25
So basically I partition the external, and instead of installing the OS on the hard drive on my laptop, I can select to do it on the external, the proceed like a normal install. Now I do this every time with a different OS, I do the same thing right? And on the BIOS screen I got to select to boot from USB right?

---

### Post by oldfred on 2010-10-25
You will just have to decide which system's boot loader to use, either the last install or one you select and then not let the others install to the MBR. Grub2 is better at finding other systems, if you install grub legacy you will probably have to manually add boot stanza's to boot other systems.

---

### Post by Jetso on 2010-10-25
I'd rather us GRUB2, as I am more used to it... is there a way I can always keep GRUB2. I know OpenSUSE doesn't use GRUB2, and that is one of the things I was inntrested in installing.

---

### Post by oldfred on 2010-10-25
I have not installed Opensuse, but most distributions give you an option on where or whether to install its bootloader (grub or grub2).

If you do not have an Ubuntu based install you can create just a grub2 boot partition but it then does not update automatically.

If you do overwrite the MBR you can always just reinstall grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Jetso on 2010-10-25
Well I plan on putting 3 operating system on it. Ubuntu, which I will build the Chromium OS on, and have that replace it. OpenSUSE, and Linux mint, as my last venture didn't go so well. If I install Ubuntu last, that will make sure I have GRUB2 won't it?

---

### Post by Fafler on 2010-10-27
I haven't read this thread entirely, but if it haven't been suggested, install each grub on partition for the first two distributions and then install the last one on the MBR. The GRUB on the MBR should automatically be able to chainload the other bootloaders, keeping each distribution completely separated.

---

