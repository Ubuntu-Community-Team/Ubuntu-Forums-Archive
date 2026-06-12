---
title: "[SOLVED] Installing Fedora with WinXP and Ubuntu 8"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by sjbaugh on 2008-09-11
I have a PC on which I have installed WindowsXP (first) and then Ubuntu 64 bit Hardy Heron.

I am running Fedora 9 in VirtualBox under Ubuntu so that I can test the programs that I write under Ubuntu on a Red Hat/RPM based distro. I am finding some difficulties in access to hardware (Particularly USB and sound is iffy) so I would like to install Fedora9 in its own partition (I have plenty of free disc space), but still having Grub boot Ubuntu by default with the option of windows and Fedora. I don't want to re-install the WinXP or Ubuntu.

Is this possible without jumping though to many hoops? If so what is the best way to go about it? (has anybody done it?)

Thanks, Steve, England

---

### Post by Pumalite on 2008-09-11
Use Gparted Live CD to allocate free space for Fedora. Once Fedora is installed; you'll have to reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by sjbaugh on 2008-09-11
Thanks, I will give that a try when I am feeling brave!

---

### Post by Pumalite on 2008-09-11
It's better to die on your feet than to live on your knees.
(don't forget to backup everything before you start. It takes a while)

---

### Post by caljohnsmith on 2008-09-12
Sjbaugh, actually you can save yourself from having to reinstall Grub if you have Fedora install its Grub to its own partition, and not the master boot record (MBR). That will also make it extremely simple to boot Fedora from your Ubuntu's menu.lst, because all you need to do is add an entry like:
```
title Fedora
root (hdX,Y)
chainloader +1
```
You don't have to mess with kernel and initrd lines, not even kernel options, since Fedora will do all that for you when it installs Grub. The trick to installing Grub to the partition boot record (PBR) instead of the MBR is during the Fedora install process, tell it to install Grub to (hdX,Y) where that is your Fedora partition, and not (hd0) which is the MBR. If you need any more details/info, let me know, otherwise let us know how it goes. :)

---

### Post by sjbaugh on 2008-09-12
Thanks, I shall have a go over the weekend, I have already downloaded Gparted .iso file and burnt a CD, but not yet done the re-partion as I have to do a back up first.

Thanks to all, Steve

---

### Post by sjbaugh on 2008-09-12
Pumalite, caljohnsmith,

The installation worked fine. I re-partitioned the disc to give me 50GB of free, unpartitioned space and then ran the Fedora Install. I chose the option to install to free disc space and then to put the boot loader in dev/sda3. After the install I had to do a re-boot. At this stage I booted into Ubuntu.

I then (after first making a copy of the file) I edited the menu.lst file using:

```
cd /boot/grub
sudo gedit menu.lst
```

At the end of the file I appended:

```
#added to enable boot into fedora
title        Fedora
root        (hd0,2)
chainloader    +1
```

The 0,2  (disc 0 partition 2) might be different for another configuration.

A re-boot now gave me this extra "Fedora" option on the grub boot screen. Selecting this then gave the Fedora boot screen from which I could boot Fedora and complete the installation.

I have added the extra detail in case it helps someone else.

Thanks to you both,

Steve

---

### Post by caljohnsmith on 2008-09-13
Thanks for following up and letting us know you got things working, Steve. That will help other people who stumble on this thread if they have a similar problem. :)

---

