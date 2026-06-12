---
title: "GRUB - can not install"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by gonesolo on 2006-12-19
ok so I've D/L 6.10 and the CD boots fine. I've checked the CD and it passes the media test. 

the install goes great right the way to the end but lets go back a bit. 

I have two sata hard disks (sda & sdb) with Windows Vista RC1 installed on sda.

I'm trying to install Edgy on sdb. When the partitioning screen comes up I can see both disks and I've created the default disk config on sdb.

When asked if I want to use GRUB I say yes and the installer asks where to install it. However it defaults to hda (which I think is my DVDR/W) now I've tried changing it to all of the following

sda
sda1
sdb
sdb1

however when the install gets to the point of writing GRUB to the boot drive it fails with something along the lines of (sorry at work not in front of PC)

Unable to install GRUB

Fatal error - setup can not continue.

This setup has worked before, the only difference I can think of is before now I was running Windows XP but now I am running Vista on the hard disk.](*,)

---

### Post by Herman on 2006-12-19
Hello gonesolo,
 It's good that you are installing Ubuntu and installing Grub to MBR. :D
Here is a link about how to dual boot Ubuntu with Vista, you should look that over and see if there is anything there that might help, [B][http://tinyurl.com/hrbhy](http://tinyurl.com/hrbhy)
[/B]
Are you using the 'Alternate' install CD?
The 'Alternate' CD should be offering to 'install Grub to MBR on your first hard  drive', if that's the CD you are using. Last time I checked, the 'Desktop' Live/Install CD didn't offer any options about where you can install Grub, so I don't think you mean that one. There could be lots of things I don't know about the 'Desktop' installer though. :D

If you are using the 'Alternate' CD, you should be able to specify where exactly you want your bootloader installed by using the following selections, 
For MBR on first hard disk - accept default and just choose <Yes>
For options choose <No>
For Lilo choose <Go Back>

If you chose <No> for a new window where you can specify somewhere else to install Grub, you can type,
second hard disk MBR .........(hd1)
third hard disk MBR.............(hd2)
floppy disk.........................(fd0)
first hard disk, second partition...(hd0,1) or /dev/sda2 (if that's your Ubuntu partition.

You can't just type ' sda', 'sda1', 'sdb', or 'sdb1'. That would not be correct syntax.

You can type, '/dev/sda', that should work.
It is pretty well explained if you read the sign here,
[IMG]http://users.bigpond.net.au/hermanzone/p6/10mbr.png[/IMG]

I hope that will help you, or am I misunderstanding your question?

Regards, Herman :D

---

