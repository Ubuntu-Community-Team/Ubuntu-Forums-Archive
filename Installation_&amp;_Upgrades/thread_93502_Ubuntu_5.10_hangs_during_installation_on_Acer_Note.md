---
title: "Ubuntu 5.10 hangs during installation on Acer Notebook"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by Timokl on 2005-11-22
Dear Community,

I hope someone can give me a little help to let me make my first steps into the Linux world.

Last week I have bought a new notebook, Acer Aspire 5021NWLCi, which has a AMD Turion 64 CPU (technical data: [http://www.acer.co.th/product/travelmate/aspire5020/index_p.htm)](http://www.acer.co.th/product/travelmate/aspire5020/index_p.htm)). But I cannot get the installation running, because at some point after installing the base system, the whole computer suddenly comes to a complete stop.

**What I did:**

I downloaded the .iso from Ubuntu 5.10 for AMD64 cpus and burned it onto a cd on Windows (using Nero, in case that matters).

I booted from the cd, and started a normal installation by pressing return at the prompt.

At first, the installation runs smoothly. Because I need an installation of Windows on my computer for work, I want to do a multi OS installation. So I partitioned my hard drive this way:

10 GB primary partition (Windows already installed, NTFS)
10 GB logical partition (jf3 file system for ubuntu)
500 MB swap partition
30 GB logical partition (NTFS, intended for data)

The ubuntu install installs the base system, then it is about to install the additional packages (firefox and the like) -- but suddenly the LED's from both hard drive and dvd drive go blank and nothing happens any more.

This happens not always at the same time. Up to now it happend at 14% completion of this task, at 70%, at 74%, etc.

**What I achieved**

As the installation of the base system went smoothly, I decided to try the minimum installation and made the server installation at the boot prompt. This time, everything went well. I can choose now during the booting process between various ubuntu modes and windows xp through grub.

But how can I install the GUI for ubuntu. I am no Linux guru. I can copy files and decompress file with gzip at the terminal, but that's about it. Anyone to give me a hint or an advice how to "complete" the installation?

Thnx a lot in advance for your help!!!

Greetz from Bangkok,
Timo

---

### Post by magicfab on 2005-11-22
After you have logged-in to your server installation, you should perform these commands:

[LIST=1]
[*]sudo apt-get update
[*]sudo apt-get upgrade
[*]sudo apt-get install ubuntu-desktop
[/LIST]

The first two commands will bring your system up-to date.

The last command will install all the required packages for Ubuntu (Gnome-based). If you prefer Kubuntu (KDE desktop), use kubuntu-desktop in the last command. There's also xubuntu-desktop if you want a faster, lighter desktop environment based on XFCE. 

After doing this, reboot the computer with this command:
sudo reboot

Also check the wiki for more documentation and information:
[http://wiki.ubuntu.com](http://wiki.ubuntu.com)

---

### Post by Colli on 2005-11-22
My aspire did that also.  It hangs with a strange screen?

Look in the help at install.

It was something like the command:  linux vga=771 (not sure about the number 771, but look at he help at install).

That helped for me.

---

### Post by Timokl on 2005-11-25
These sudo commands were a great help! This is my first posting with Ubuntu! Hooray!!!

---

