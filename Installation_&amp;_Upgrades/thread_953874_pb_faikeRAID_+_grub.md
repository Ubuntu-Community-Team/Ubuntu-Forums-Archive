---
title: "pb faikeRAID + grub"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by pvanzini on 2008-10-20
Hi,

I'm new and it's my first post :-)
then...

I installed ubuntu 8.04.1 using all tutorials to be able to install my fakeRAID correctly using dmraid and grub...
Then it was perfect and running :-)

Problem : only my root partition was available and not the other ones previously created (----Volume01, -----Volume02,...)

Then I have updated my menu.lst (grub one) to change it a bit.
But I change it too much and now I'm no more able to reboot and got an error at bootup....

PROBLEM:
To correct, I launch the live CD. But now, I'm no more able to access to my "RAID disks" (---Volume01,...). Then I'm no more able to restore my menu.lst file at least to previous version... :-(
How to be able to view again my "disk" in /dev/mapper ? on live cd...
or other solution, objective is to be able to correct my menu.lst file...

thanks

---

### Post by dstew on 2008-10-20
If you boot the live CD, and want to use your fakeRAID volumes, you need to install dmraid, just like you did when you created them in the first place. The Live CD does not have dmraid installed unless you do it (use Synaptic). Since it only installs it to its ramdisk system, dmraid will disappear when you shut down the live CD system. You have to install it each time you boot the Live CD.

---

