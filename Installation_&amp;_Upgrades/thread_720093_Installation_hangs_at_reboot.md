---
title: "Installation hangs at reboot"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by bbrandtma on 2008-03-09
Greetings,

So I have this pile of Toshiba 3020CT laptops (thinner and lighter than the Macbook Air :-) with the AWESOME power of a 300MHz Pentium MMX and a whopping 96M of RAM. I have been running DamnSmallLinux, but its kind of restrictive.

I figured out how to install Xubuntu 7.10 from a hard drive partition and everythings goes great until several hours later when it gets to:

Sending SIGKILL to all processes.
Please standby while rebooting the system.

It just hangs there forever, and if I do a manual reset (using the Bill Gates paperclip) it waits a long time at the splash screen and drops me to BusyBox.

Using "recovery mode" I get the following message at the end:

ALERT! /dev/disk/by-uuid/{big hex string} does not exist.

I rebooted into DSL by running it on the pendrive and looked at /mnt/hda1/dev and found the entire "disk" directory is missing. It seems the installation didn't finish.

I have a slightly newer Toshiba 3110CT (300MHz Pentium II with 128M of memory) and the installation works just fine.

THANKS for your help.

Bill

---

### Post by makkan77 on 2008-03-12
> **bbrandtma said:**
> ...the splash screen and drops me to BusyBox.

Using "recovery mode" I get the following message at the end:

ALERT! /dev/disk/by-uuid/{big hex string} does not exist.

I rebooted into DSL by running it on the pendrive and looked at /mnt/hda1/dev and found the entire "disk" directory is missing. It seems the installation didn't finish.

I have a slightly newer Toshiba 3110CT (300MHz Pentium II with 128M of memory) and the installation works just fine.


I also have an old Toshiba laptop (Satellite 320CDS, 233MHz Pentium MMX, 96 MB RAM and so on). And I've experienced a similar problem with almost all flavours of ubuntu since 7.06. 

I found a way to continue the boot process in this ** LINK: **[forum ]("http://ubuntuforums.org/archive/index.php/t-414903.html"). 

In short when dropped to busybox issue the following commands: 
[INDENT]
modprobe ide-disk
modprobe ide-generic
mount -t ext3 /dev/hda1 /root [/INDENT]

**NOTE** You should ofcourse change ext3 to your fs-type and /dev/hda to whereever the drive you're trying to boot is located. 

then to continue booting press CTRL-D

This has always worked for me. Also I found that one could replace the initrd image in boot using yaird. But I don't want to break your system so I leave that up to you since I have no idea what it actually does (but it works).

---

### Post by makkan77 on 2008-03-13
Actually I tried a different approach when I got home yesterday and it turns out all you have to do to continue booting is: 

modprobe ide-generic

then hit CTRL-D to continue booting.

---

### Post by makkan77 on 2008-03-14
I've also found another way to make this problem go away permanently (a way I actually understand whats happening).

As I wrote in the previous post the problem is that the kernel modules for ide are not loaded when they are needed. 

for that you must edit /etc/mkisofs-tools/modules

and add the modules you need, I added: 
ide-core
ide-generic
ide-disk

After that is done you need to make a new initrd image. Issue the following command:
sudo dpkg-reconfigure linux-image-$(uname -r)

Now on the next reboot you should be able to startup without any problems.

---

### Post by FactTech on 2008-05-19
Many thanks to Makkan77 -- I was able to use a modified form of your advice to get Fluxbuntu up and running on a Toshiba 335CDS (with upgraded RAM and HD).

This type of problem seems common to many Toshiba laptops. For those experiencing similar issues (successful install, but drops to busybox complaining about missing UUID on boot from hard drive), note that if executing 'modprobe ide-generic' from busybox then exiting boots as normal, the following permanent fix will probably work:

[REMINDER: These instructions are for FLUXBUNTU]
1) cd /etc/initramfs-tools
2) sudo cp modules modules.backup
3) sudo leafpad modules
 3a) In leafpad, add the line 'ide-generic' at the end of the commented section (last line), save and quit
4) sudo update-initramfs -uv

After I did this, the laptop boots without trouble.

---

