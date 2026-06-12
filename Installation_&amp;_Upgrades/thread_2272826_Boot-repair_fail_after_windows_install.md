---
title: "Boot-repair fail after windows install"
date: 2015-04-08
forum: Installation &amp; Upgrades
---

### Post by DataMonkey on 2015-04-08
Hi all

I reinstalled windows 7 from usb yesterday as it had become unstable. I have done this a few times before and had no trouble. In the past I have restored grub via terminal from the live CD but this time I used boot-repair. I think I have made a mistake somewhere as the partitions no longer seem to have my Ubuntu 12.04 boot partition. I thought it was sda1, which is the correct size, but sda1 now shows up as an extended partition. I hope I can restore Ubuntu without reinstalling!

The boot-repair info url is:

paste.ubuntu.com/10777937/

Any help would be fantastic!

Cheers

---

### Post by tim105 on 2015-04-08
There probably is a solution that involves running commands, but I find this a lot easier:

Boot into W7 
Download and install EasyBCD 
Add Linux to the boot manager.

Here is a screenshot if you need guidance (numbered steps for you):
[IMG]http://s28.postimg.org/hasiiua7h/easybcd_add_entry2.png[/IMG]

---

### Post by oldfred on 2015-04-08
Your partition is missing. And that is because Windows does not correctly see Linux partitions, so it rewrites partition table without your Linux partition.
Your sda1 shows a large gap from start of extended to start of swap. That is where your Linux partition was.
Was your Linux partition sda1, primary? or sda5, logical?
It makes a difference as if sda1 the Linux partition will start at sector 2048, if sda5 it starts a few sectors after 2048. And then how you recover it matters.

You should be able to use testdisk to find missing partition. But need to know if primary or logical.
       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Testdisk is in repository, so you can just install into Ubuntu live installer. It often is included in other Linux repairCDs.

---

