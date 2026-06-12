---
title: "Frugal UNetbootin Xubuntu 10.04_NetInstall on an old laptop?"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by brynjarh on 2010-07-28
I'm planing on installing Xubuntu on an old laptop that can't boot from CD or USB, I'm afraid to brick the computer so I'm posting how I'm going to install it and see if anyone spots something I might be doing wrong, never done a frugal install before, I also have one question.

[LIST=1]
[*]From windows, download UNetbootin for Windows [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[*]Select Distribution, Ubuntu, 10.04_NetInstall
[*]Select Type: Hard Disk and then probably drive C: or something.
[*]Press OK and reboot.
[*]Boot into netinstall.
[*]Install base system or something like that.
[*]Install Xubuntu on top of that by selecting it from a list of options.
[*]Done!
[/LIST]

One thing I'm wondering, the 10.04_NetInstall loads entirely into RAM right, Even if I select Hard Disk and drive C: ? Which allows me to do whatever to the hard drives partitions from the installer since it's entirely in RAM right?

---

### Post by snowpine on 2010-07-28
You can't install onto the same partition from which you are running the installer .iso, sorry. :(

One option is to get an enclosure or connector for your hard drive (they are inexpensive), pop the drive out, and use another computer to install. (You should probably disconnect the hard drive on that computer unless you have a strong understanding of GRUB.)

---

### Post by brynjarh on 2010-07-28
> **snowpine said:**
> You can't install onto the same partition from which you are running the installer .iso, sorry. :(

Are you sure? Note that I'll be using the net_installer which is only about 12mb which I think means it wont be running from the partition, it will be loaded from the partition into RAM and executed from there, leaving the partition free to be edited.

Also I quote [http://sourceforge.net/apps/trac/unetbootin/wiki/installmodes](http://sourceforge.net/apps/trac/unetbootin/wiki/installmodes) 

> If you want to make a full, standard install and can't use a Live USB drive as your installer, you can still use a frugal install as the installer (with some extra work needed for partitioning). The particular details of this task depends on the boot mechanism used by your distribution (as you are unable to repartition your drive while it's mounted). Again, this issue only arises if you're installing to hard disk from a frugal install, and not if you're installing to hard disk from a Live USB.

First, let's distinguish between two separate types of distributions:

Distributions loaded entirely into RAM: These distributions load everything into RAM and run directly from there. Since they don't need to access your hard drive partition, it remains unmounted, and hence you are free to repartition your hard drive (using the installer or GParted) while they are running. These tend to be the smaller distributions, such as Parted Magic, Slitaz, Puppy Linux, and DSL. A few distributions, like PCLinuxOS, also have a copy2ram boot option that will make them behave like this. Additionally, Ubuntu and Debian's netboot installers (listed as the NetInstall? option in the UNetbootin versions menu for those distributions) also run entirely from RAM (but the standard desktop, server, and alternate installers do not).

Distributions that need access to the source medium while running: These distributions will need access to the source medium (in this case, your hard drive) while they're running. As such, your hard drive partition will remain mounted while the distribution is running, and you won't be able to repartition it. The Live CD and installer iso files for basically all major distributions, including Ubuntu, Fedora, Linux Mint, and Sabayon belong to this category.

**If you're simply trying to install a mini-distribution that's loaded entirely into RAM, or will be using the netboot installer for Ubuntu or Debian (listed as the NetInstall? option in the UNetbootin versions menu for those distributions) rather than the standard desktop iso, then you don't need to read further, as you shouldn't run into any partitioning issues; just use the Hard Disk install mode to make a frugal install, boot and run the installer, and install to hard drive as usual.**

---

### Post by snowpine on 2010-07-28
I stand corrected; good luck! :)

(edit)ps If it doesn't work, see my previous post about installing on another computer using an external drive enclosure.

Also make sure you compare your hardware against [the Xubuntu system requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20GUI%20alternative%20%28Xubuntu%29") before you get too far in the process.

---

### Post by linux18 on 2010-07-28
If there is a linux swap file, linux will use that as a temporary storage, consider doing all of your partitioning first and  really really defrag XP before partitioning. In case something goes wrong, have the netboot image already ready to go on the next boot. And if i were you I'd have two netinstall images on the hard disk, in case one doesn't work. Also, are you sure that it can't boot from a usb? did you check the bios and change boot order?

---

