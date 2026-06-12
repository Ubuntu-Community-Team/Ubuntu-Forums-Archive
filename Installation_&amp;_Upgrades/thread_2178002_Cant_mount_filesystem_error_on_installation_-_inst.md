---
title: "Cant mount filesystem error on installation - installing on windows xp machine"
date: 2013-10-01
forum: Installation &amp; Upgrades
---

### Post by castor2 on 2013-10-01
I use Windows 95 as my primary operating system and tried to install ubuntu linux 13.04.


  When I booted the computer with USB (created using universal usb  installer), I get "Can't mount filesystem" error. I tried creating  another bootable usb of boot-repair-disk-32bit.iso, and tried  recommended repair option. It said that the errors have been fixed, but  when I try again, I get the same error.

  
Here is the URL that the repair tool generated. [http://paste.ubuntu.com/6179880/](http://paste.ubuntu.com/6179880/)

  
I really want to give linux a shot, but its giving me a hard time.

---

### Post by Bucky Ball on 2013-10-01
*Thread moved to **Installation & Upgrades**.*

Welcome to the forums.

From your post it is unclear what exactly you are doing. Are you installing Ubuntu to a separate partition, dual-boot with Windows, or are you trying to install Wubi, Ubuntu as a program in Windows?

Win95 is so old (and unsafe, incidentally) unsure whether the Wubi option will work. Also, Wubi designed to try before you install, not a permanent solution. Just try Ubuntu from the install media, if you like it, install it to a partition. You won't get much help with Wubi as not many people use it and it is phased out as of the next release (or may even be as of 13.04).

---

### Post by castor2 on 2013-10-01
Thanks for the response.

I downloaded the 32bit iso file from Ubuntu 13.04. I am trying to make a fresh installation from bootable usb, which I made from the ISO.

I am presented with two options, 1. try ... and 2. Install. I tried both and they give me the same error message. Can't try to mount filesystem.

I tried the repair tool which said it fixed, but apparently nothing changed. Here's the info from the repair tool. [http://paste.ubuntu.com/6179880/](http://paste.ubuntu.com/6179880/)


Here is some more output:

> General error mounting filesystems.
A maintenance shell will now be started.
Ctrl D will terminate this shell and will reboot.

---

### Post by Bucky Ball on 2013-10-01
You have a 32bit machine? If not, you should be using the 64bit (disregard the advice to use 32bit). Although that, I don't think, is your problem, it is what you should be using. The AMD64 version, regardless of processor make.

You can't try a disk? Anyhow, 'Try Ubuntu' should be booting directly from the USB so let's concentrate on that. This does seem strange, from your boot-info:

> Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sdb.

and:

> Boot sector type:  SYSLINUX 4.06
Boot sector info:  Syslinux looks at sector 32776 of /dev/sdb1 for its 
                       second stage. _The integrity check of Syslinux failed. _
                       No errors found in the Boot Parameter Block.

The underlined is where it's falling over. In other words, the boot sector on your install media is failing. So that indicates the USB dongle, not the machine and there appears to be nothing untoward with your partitioning or system (that I can see), apart from the fact that you have nowhere to install Ubuntu even when you do get this working!

[*Note on that*: Make some room. If you're not using WinXP then boot into Windows and make some free space, create an extended partition the full size of the free space, then get back to this. This should make four partitions all up on that drive. You don't want any more. Ubuntu will go on virtual partitions you create inside the extended one. Not complicated.] 

At the list of options, could you try hitting 'Check install media for defects' option rather than 'Try' or 'Install'? I'd also be tempted to try another USB dongle if you have one, or a CD/DVD. 

And the 64bit ISO if you are running 64bit.

---

### Post by castor2 on 2013-10-02
I ran a MD5 check on the downloaded iso and it differed from the one on the ubuntu site. I downloaded the copy again, this time through utorrent, and the installation went fine.

Thanks a bunch for pointing it out. Appreciate your help. I hope I can learn to use linux and will ditch Windows forever soon.

---

