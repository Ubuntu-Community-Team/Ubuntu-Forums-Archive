---
title: "no init found, try passing init= bootarg in Maverick 10.10"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by peer30 on 2012-04-23
I've got Ubuntu 10.10 Maverick Netbook version for a rather long time on my Dell  Inspiron Mini 1010, it has always been OK and is effectively the last version of Ubuntu working well on this small laptop, according to Ubuntu itself.
Yesterday however my touchpad was strangely functioning and suddenly the laptop shut off. 

Now when I start the laptop I get:
> no init found, try passing init= bootargI have actually read a lot about this problem, also that the so called 10.10 live cd should have a bug.
But it is the only CD (Netbook live cd) who is actually working, older versions of Ubuntu live cds "as advised" did not start up at all or are missing files.
Even the so called Knoppix live cd is not functioning at all.

The only one working well is the Ubuntu 10.10 Netbook live CD.
In the terminal I did "sudo fdisk -l", the result was:
[INDENT]> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (minimum/optimal): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008b4ea

Device               Boot            Start                End                       Blocks                     Id                      System
/dev/sda1         *                   1                       19076                   153219072            83                      Linux
/dev/sda2                               19076             19458                   3068929                   5                      Extended
/dev/sda5                                19706             19458                  3068928                82                       Linux swap / Solaris[/INDENT]When I insert after in the terminal "sudo fsck /dev/sda1" I get:[INDENT]> fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010(
fsck.ext4: Device of resource busy during opening /dev/sda1
Filesystem exclusively mounted or opened by another program?[/INDENT]Reboot does not work after, I constantly get the same error as before.
It looks as if the grub has been destroyed, I shortly see Ubuntu on screen and then there's the init failure.

I also tried to re-install everything, but this stops in the beginning, that is to say, when you&#341;e asked if your laptop has been connected with the internet, that the laptop has been connect directly to electricity, if you want to install new updates and certain sortware from third parties.
The mouse pointer constantly "rolls and rolls" and nothing happens at all after. 

What's the matter now?

When I try to open the HD in the live CD screen I get:
> Error:
UNABLE TO MOUNT 157 GB FILESYSTEM
A job is pending on /dev/sda1I like to read a good solution, as I am very dependent of this small laptop for my job. Fortunately there are not any important on the HD now, as I recently burnt these on a data-dvd.

Thanks for all your replies, looking forward to all the possible solutions.

---

### Post by peer30 on 2012-04-29
It has been solved now, with the SystemRescueCD, so everything works fine again on my Dell mini laptop.

---

