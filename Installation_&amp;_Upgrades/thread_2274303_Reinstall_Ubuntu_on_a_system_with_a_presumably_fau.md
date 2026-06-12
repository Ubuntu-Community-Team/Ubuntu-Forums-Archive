---
title: "Reinstall Ubuntu on a system with a presumably faulty MBR and misaligned partition"
date: 2015-04-19
forum: Installation &amp; Upgrades
---

### Post by ALeX850 on 2015-04-19
Hi!

I have an Acer computer with a dual boot Windows 7-Ubuntu 13.04
Getting some troubles to start up Windows 7, I decided to give Acer Windows Recovery a try so I booted my system on this partition, but no available option fitted what I was looking for, so I eventually discarded this tool just by cancelling it on the very first windows without touching anything. To my surprise, when my computer rebooted just after that I got a "No such partition Grub rescue :>" message. Something had affected Grub...
Then, I started my system on a Ubuntu 14.04 LiveUSB, and gparted showed me this:

[IMG]http://img15.hostingpics.net/pics/771943Screenshotfrom20141217163946.png[/IMG]

My Linux partition is apparently detected as "unallocated".
I subsequently used testdisk for more details, and I actually could trawl through my Linux partition thanks to it, just having some "deleted" folders... So what happened is most likely an MBR corruption. 
But frankly, I try to play around with testdisk and I can't find a proper way to repair the boot. As for me, my 3 windows partitions should be primary and Linux and the Linux swap should be logical, I think I let ubuntu make a default installation back then when I set up my dual boot.

[IMG]http://img15.hostingpics.net/pics/406860testdisk3.png[/IMG]

Anyway, I would like to reinstall ubuntu properly but since I'm not sure about the actual state of my system I'm hesitating a bit. What I would like to do is unlock the swap partition in order to delete it with gparted for having free space after my /dev/sda3 partition and then reinstall ubuntu on the free space. 
But since this so-called unallocated partition has still a proper linux structure into it, I suspect some irregularities to arise in the process.
Moreover the partition is not perfectly aligned:

[IMG]http://img15.hostingpics.net/pics/897380fdisk.png[/IMG]

Finally, I would like to know if I could just do like I described without any risks, or are there some additional steps I must take care of beforehand? 
Thanks for your help!!!

---

### Post by TheFu on 2015-04-19
Support for 13.04 ended over a year ago. [http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)  Best to run only LTS releases if you are like me and don't want to be forced to install a new OS every 6 months to retain support.

For simple boot issues, boot-repair is the easiest solution. Links below.

---

### Post by oldfred on 2015-04-19
Windows rewrites partition table and likes to leave off the Linux partitions. 

You can just in testdisk make the Linux partition logical and it may work again. If you did not write a Windows boot loader to MBR and still have grub, some have just had it work.

But as TheFu comments you are running an obsolete version and need to reinstall with a newer version of Ubuntu.

---

