---
title: "Acer Aspire 1682"
date: 2014-07-29
forum: Installation &amp; Upgrades
---

### Post by vinx2 on 2014-07-29
Hi,
I've got a pc acer aspire 1682 wlmi, 512 MB RAM, Intel Processor 1 core no PAE. This is an old machine with windows xp running on, it is a bit slow and what is worse is that from the last 08th Aplril Microsoft will not realise further updates for xp, so I decided to install a linux distribution on my machine keeping windows too.
My pc has a BIOS which support boot from CD, but it does not run, it does not support boot from USB. My only chance is boot the system from hard disk and I read UNetbootin give the possibility to do that, that is one can install a SO without CD or USB.
I followed the instructions on the website, this guide [http://sourceforge.net/p/unetbootin/wiki/installmodes/](http://sourceforge.net/p/unetbootin/wiki/installmodes/) in particular for hard install mode.
My problem comes up when the partitioning process starts, in fact it can not mount the system in the ext4 partion I created previously.
I tried xubuntu 12.04, because it is a non pae kernel, however I tried the live version and it works; meaning that it starts works in live mode but does not install; the net HdMedia and NetInstal versions, both do not work saying they need a PAE Processor.
Any suggestions?

---

### Post by mörgæs on 2014-07-29
Hi, welcome to the fora.

Here's something about the [PAE]("https://help.ubuntu.com/community/PAE") problem. Easy to solve.

Unetbootin is a tool for creating a bootable USB stick. Probably not relevant for you.

---

### Post by vinx2 on 2014-07-29
The principal use of UNetbootin is to create a bootable usb, however, I read it can also be used to install a SO without using cd or usb for booting.
It give the chance to create a frugal install on the hard drive and make from this a proper install afterwords.
I suppose I mistaken something while partitioning, because I am anable to give the mount point.

---

### Post by yancek on 2014-07-29
If I understand your post correctly, you have done the frugal install of  Xubuntu on your windows xp partition and when you boot you have an option to select to boot Xubuntu?

Have you created a partition on which to install Xubuntu or are you doing that during the install?  Or do you have free/unallocated space on which to install.  I'm not sure what you mean by unable to give mount point.  There should be a specific option where it shows Mount point and you select one of the options.

---

### Post by mörgæs on 2014-07-29
> **vinx2 said:**
> I read it can also be used to install a SO without using cd or usb for booting.

SO, is that OS, operative system? 
Please post a link.

---

### Post by vinx2 on 2014-07-29
I've downloaded UNetbootin for Windows, started the program which make you select a distribution to download, I chose Parted Magic, once the process has terminated the system rebooted and made me choose between starting Windows or UNetbootin, I've chosen the second option.
Parted Magic started and I created a partition for linux, ext4 file system, and another one for swap. I rebooted the system again, this time I made windows to start.
With windows running, I uninstalled UNetbootin and installed it again, started the program and this time I chose to download xubuntu 12.04 live, while in type option, on the bottom, I chose hard disk.
Once the process is terminated the system rebooted. Now it gave the two option once more: start windows or UNetbootin, I chose UNetbootin. This time I had various option, two of them were, Install xubuntu or start the live without installing, I chose install. However, I also tried the live and it works properly.
Anyway, with the install option, the installation process starts, everything gos well until the partitioning process. At this stage, it should have made me mark the linux partition ( ext4 file system) with root "/"  to have the mount point. Is that right? 
What happened insted was that, the program asked me which partition I wanted to install the bootloader, I gave it all the options I had at a time and it failed with each of them.
At that point the program did not runned further and I had to stop the system manually.

---

### Post by vinx2 on 2014-07-29
Sorry, I wrote SO, but I meant OS, Operative System.

---

### Post by mörgæs on 2014-07-30
I think the safe approach is booting from a CD using the *forcepae* option. Exactly what happens when you try?

---

### Post by oldfred on 2014-07-30
You install grub2 boot loader to a drive like sda, not to partitions like sda1 or sda2. And if you installed to the XP partition you corrupt XP and may not be able to boot. Never install grub to a NTFS partition.

---

