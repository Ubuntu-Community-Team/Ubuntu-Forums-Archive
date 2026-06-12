---
title: "Installing 20.04"
date: 2020-11-23
forum: Installation &amp; Upgrades
---

### Post by avhation2 on 2020-11-23
Hi,
Twice I have failed to install 20.04 - when restarting after several  installs I get this message attached below.  Can anyone help?
 
[IMG]https://ubuntuforums.org/images/attach/jpg.gif[/IMG] IMG_20201123_175935460.jpg (64.4 KB)

I am using a new 1Tb SATA HDD, partitioned during the installation with Swap 8Gb, root for the OS 6Gb, home for the data 250 Gb,  and unallocated 700+Gb

---

### Post by CelticWarrior on 2020-11-23
Root is absurdly low. Give it at least 25-30GB.
A separated swap partition is no longer needed.

That said, the above likely has no effect on your issue. Your issue is the graphical interface not loading and the reason is probably related with some specific hardware.
Please post your hardware specifications, particularly the graphics.

---

### Post by ActionParsnip on 2020-11-23
You don't need a swap partition but can use one. 50Gb root, 8Gb swap, rest for /home (assuming desktop use)

---

### Post by mrdc76 on 2020-11-24
The optimal size of swap is 1-2 GB for most use cases regardless the amount of RAM.

---

### Post by CelticWarrior on 2020-11-24
> **mrdc76 said:**
> The optimal size of swap is 1-2 GB for most use cases regardless the amount of RAM.

Indeed.
Currently Ubuntu uses swapfile instead of a separated swap partition and the optimal size is set automatically.

---

### Post by avhation2 on 2020-11-24
Thanks CW.  Clearly I misunderstood the recommendation elsewhere that I should make Root just sufficient for the OS which I thought was only 4 Gb or so  but I should have allowed extra for it to actually operate perhaps. 

My hardware is an old Dell 380 with Pentium4 CPU 3.0 Ghz, RAM 4 Gb (which is why I chose 8Gb of Swap).  The BIOS tells me nothing about graphics so I imagine it is very basic and built into the motherboard. It's apparently a 64bit machine. 

I have reloaded 20.04, without trying to be clever by choosing optimum  partition sizes and settings myself, and now have the OS running OK.  So I  intend to try and change the partition sizes and positions to achieve my aim which is to separate the OS from my data to avoid upsets when updating the OS in future, and join up the bits of wasted partition space  Having read your later message, I guess I must already have the optimal partitioning so perhaps I should leave it all alone and just hope for the best (and rely on backup)  when updating in future? I've taken a picture of the 5 partitions but no joy with copying it to here.
Anyway, thanks to all for your prompt advice.
Regards,
Henry

---

