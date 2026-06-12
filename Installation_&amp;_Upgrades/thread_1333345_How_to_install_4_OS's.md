---
title: "How to install 4 OS's?"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by nelson2006 on 2009-11-21
Hello everyone, I've just bought a brand new pc :D (with Windows Xp) And I would like to know how can I install Windows 7, Ubuntu 9.10, Opensuse 11.2, Fedora 12 and a partition for all my music and videos the best way and order possible? The hard drive's 320 gb. I was thinking of 20 gigs for each OS and the rest for the other partition ;). What's the best order to do it? Where do I create the other partition :-k?

---

### Post by lmarmisa on 2009-11-21
If you plan to use several OS, may be you need a virtual machine type solution. With virtualization you can create as many virtual machines as you want (with different operating systems).

I would recommend you [http://www.virtualbox.org](http://www.virtualbox.org)

Saludos desde Madrid

Luis

---

### Post by oldfred on 2009-11-21
If you do not want to try virtual.

I do not know if openSuse or Fedora need primary partitions. Windows does. Ubuntu does not. I think openSuse or Fedora want to make a boot partiton, windows 7 if a clean install wants to create a boot partition, but if you create the partition in advance it will use that without the boot partition.

You will need lots of tools to recover MBR.
restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

And a bunch of links that I have referred to on multibooting:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

---

### Post by steveneddy on 2009-11-21
> **lmarmisa said:**
> If you plan to use several OS, may be you need a virtual machine type solution. With virtualization you can create as many virtual machines as you want (with different operating systems).

I would recommend you [http://www.virtualbox.org](http://www.virtualbox.org)

Saludos desde Madrid

Luis

This is my recommendation also. Partition your drive for storage but for the rest I would use a VM.

7 uses a different boot loader than XP. You could jump thru hoops getting everything set up with four OS's .....

(why do you need four OS's?)

but in the end it would be faster and easier to just use VirtualBox.

I use Ubuntu with VirtualBox and run Vista and 7 from there when I need them.

---

### Post by nelson2006 on 2009-11-21
Hey, thanks a lot for the replies guys :D! My desire of installing all that is because I really don't how to handle much virtualbox :(. For me it's much easier installing on my hard drive. But I'll give virtualbox another chance :P.

---

