---
title: "Installing Grub for Dual Boot"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by Jim.Crutchfield on 2010-08-24
Hello everybody.  I'm new here and to Linux.  I've just installed Ubuntu on a WinXP machine, following the instructions at [http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation), installing Ubuntu 9.04 as recommended. Everything went fine except that when I got to installing GRUB, the instructions told me to expect this:

> -> Finish partitioning and write changes to disk -> "Installing the base system" -> ... -> 
->"Install the Grub boot loader to the master boot record?": YES -> Continue 
 
[LIST]
[*]In this step, Grub must be installed both on the MBR (master  boot record) as well as locally on the partition being installed (in  this example */dev/sda6*). The local version will be chainloaded by the MBR version. Therefore, install Grub a second time:
[/LIST]
 -> Go Back -> Install the Grub boot loader on a hard disk ->  "Install the Grub boot loader to the master boot record?": NO -> Device for boot loader installation: */dev/sda6* -> Continue 
But the installer never asked me if I wanted to install GRUB to the master boot record--I think it just did it.  And it didn't give me a chance to go back and install GRUB again in the local partition.  

Even so, the computer starts up fine, and I can choose my OS OK.  Do I need to put GRUB in my local partition?  If so, how do I do it?

I tried using GRUB-install:

> user@host:~$ grub-install /dev/sda6but that returned the following error:

> rm: cannot remove '/boot/grub/stage1' : Permission deniedI looked into file permissions, but after learning how to use GParted and messing with that all day, I just couldn't get my head around the complexities of Linux permissions.

Can somebody just tell me what, if anything, I need to do, just to get my boot-up/chainloader/whatever organized properly?

Thanks!

Regards,

Jim Crutchfield
Long Island City, NY

---

### Post by dtoronto on 2010-08-24
my understanding is that you would only need grub on the master boot record, I may not be understanding something about your particular installation, but if you can boot into both OS's then grub was successfully installed.

---

### Post by tommcd on 2010-08-24
> **Jim.Crutchfield said:**
>  I've just installed Ubuntu on a WinXP machine ... installing Ubuntu 9.04 as recommended.
Even so, the computer starts up fine, and I can choose my OS OK.  Do I need to put GRUB in my local partition?  If so, how do I do it?

So are you able to choose between XP and Ubuntu from the grub menu when the computer boots up? If so, then there is nothing more that you need to do.
By the way, You don't need to limit yourself to Ubuntu 9.04. I currently boot Windows XP, Ubuntu 10.04, Slackware 13.1, and Salix 13.1 all from the Ubuntu 10.4 grub2. If you want to continue using Ubuntu, I would just install Ubuntu 10.04.
Here are some great guides to using grub2:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
Write back if you need more help.

And welcome to the Ubuntu forums!!!

---

### Post by oldfred on 2010-08-25
Chainloading is a way to boot multiple installs using old grub. You create one grub (only) partition and boot to that partition. Then from the grub partition you chainload to each other system which has to have its boot loader installed to the partition. (This is how grub or grub2 boots windows).

You do not have to use chainloading. And if you only have one install there would be no real reason to set it up that way. The advantage of chainloading is that you have two steps to booting, a standard initial grub menu and each installs updated grub menu. The disadvantage is two menus & two levels of grub. And you have to manually create the initial grub standard menu.

With grub2 it is much better at finding other systems so you do not have to chainload. It also does not like to be installed into partitions.

---

