---
title: "&quot;No root system identified&quot; on install. How can I change windows partition to EXT4?"
date: 2017-01-26
forum: Installation &amp; Upgrades
---

### Post by mattya on 2017-01-26
I know this is probably a thread somewhere, but I didn't find the right information for my situation. I am using windows 10 and have a USB with Ubuntu on it. I have created a new partition, but I'm not sure how to change the file system to EXT so that Ubuntu will recognize it when I try to install it. Any pointers?

Also, the website I was using to hand-hold me through the process shows a screen shot with "Installation Type" during the install with the option to install ubuntu alongside windows boot manager. This is what I would like to do, but that option never comes up in my installation process. Perhaps it was part of an older version, or perhaps I have not yet come across it?

Anyway, my stuff is backed up but I'm hoping there may be an easy solution.

Thanks!

---

### Post by yancek on 2017-01-26
You don't need to create a partition for Ubuntu from windows.  In fact, I don't believe a standard windows system can read or write to any Linux filesystem.  Just leave unallocated space.  You can create the partition and format to the Linux (ext4) filesystem during the install.  If you don't see the Installation Type window immediately after  the Preparing to Install window, I suspect either a bad download or Ubuntu wasn't put on the usb correctly.  What software did you use to put Ubuntu on the bootable usb?  Also, which iso file did you download?

---

### Post by ubfan1 on 2017-01-26
Read [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

Windows must not be hibernated, so to ensure that you need to alter a power option (advanced setting).  There might be other reasons the Ubuntu installer does not see the Windows partition, like having "dynamic" vs "basic" partitions (see the Windows disk listing).

---

### Post by mattya on 2017-01-26
I used rufus to create the bootable usb and loaded it with ubuntu 16.04 amd64 desktop version (just downloaded it from ubuntu's site).

To be more precise, the menu at which the installation sticks is the allocate drive space in which "device for boot loader installation" lists /dev/sda and nothing else.

All hard drive space is listed as basic.

Thanks for the continued help. Ought I try and use a different software to create the usb?

---

### Post by oldfred on 2017-01-26
sda is always the correct place to install the grub2 boot loader on single drive systems with minor exceptions. 
On the partition you want for Ubuntu, you need to press the change button, format as ext4 and use as / (root). Usually you add something for swap. I suggest 2GB.

Often better to partition in advance using gparted, but you can add & modify partitions with the installer, but must have Windows 10 fast start up off for Linux NTFS driver to see the NTFS partition.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 10 screens or similar to Windows 8
[URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi"]http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi

[/URL]
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

[URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi"]
[/URL]

---

### Post by mattya on 2017-01-27
Still no luck. I may be over my head with this, but the install doesn't recognize the hard drive. If I run gparted from Ubuntu in the try Ubuntu mode, the hard drive is recognized and I can partition it with EXT and swap, but the installation still can't see it. I have tried turning off fast boot and secure boot, changing the BIOS/UEFI setting to CSM/Legacy, reinstalling the USB with Ubuntu, and installing Ubuntu 16.10 on the USB, all with the same issue.

Once I get to the culprit screen on the install, I can&#8217;t manually type in anything or search for the drive. 

I&#8217;ll keep trying.

---

### Post by oldfred on 2017-01-27
Fast Boot in UEFI and Windows fast start up are two different settings. Both need to be off.

---

