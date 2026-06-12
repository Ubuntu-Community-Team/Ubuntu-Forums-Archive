---
title: "How to remove installation on lower partition?"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by noisyscanner on 2011-02-24
Hey.
My partition table is as follows:

[LIST]
[*] sda1 - WinRE - Something Windows uses
[/LIST]

[LIST]
[*] sda2 - Windows7
[/LIST]

[LIST]
[*] sda3 - Data
[/LIST]

[LIST]
[*] sda4 - Extended partition:
[/LIST]
[INDENT]
[LIST]
[*]      sda5 - Ubuntu 10.04
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]    sda6 - Linux swap for Ubuntu 10.04
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]      sda7 - My /home partition
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]      sda8 - Ubuntu 10.10
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]      sda9 - Linux swap for Ubuntu 10.10
[/LIST]
[/INDENT] 
I need to remove Ubuntu 10.04 and so I therefore need to remove sda5 and sda6, right? Upon deleting sda5 in Gparted it tells me to "Please unmount any logical partitions having a number higher than 5". What is the best way to do this? Thanks
Brad

---

### Post by ajgreeny on 2011-02-24
> **noisyscanner said:**
> Hey.
My partition table is as follows:

[LIST]
[*] sda1 - WinRE - Something Windows uses
[/LIST]

[LIST]
[*] sda2 - Windows7
[/LIST]

[LIST]
[*] sda3 - Data
[/LIST]

[LIST]
[*] sda4 - Extended partition:
[/LIST]
[INDENT]
[LIST]
[*]      sda5 - Ubuntu 10.04
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]    sda6 - Linux swap for Ubuntu 10.04
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]      sda7 - My /home partition
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]      sda8 - Ubuntu 10.10
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]      sda9 - Linux swap for Ubuntu 10.10
[/LIST]
[/INDENT]I need to remove Ubuntu 10.04 and so I therefore need to remove sda5 and sda6, right? Upon deleting sda5 in Gparted it tells me to "Please unmount any logical partitions having a number higher than 5". What is the best way to do this? Thanks
Brad
Are you using a live CD to run gparted?  You will not be able to work on a partition that is mounted, and both swap partitions are probably in use by both of your installed ubuntu OSs, and will also probably be found and used by the live CD, but you can unmount them easily with a right click on each.

Incidentally you are correct about needing to remove sda5 and sda6, but next time you install a new linux OS, let it use the current swap, sda9; don't bother to make a new one, as only one swap is needed.

PS:  What are you doing with the freed space, adding it to your sda7 /home?

---

### Post by noisyscanner on 2011-03-05
Yes I'll add it to my home partition.
So if I just use gparted on a livecd to remove sda5 and sda6, then will it screw up my grub bootloader? (It'll look for Ubuntu 10.04, right?)
And also, how do I know which swap to remove, or doesn't it matter?
Thanks,

---

