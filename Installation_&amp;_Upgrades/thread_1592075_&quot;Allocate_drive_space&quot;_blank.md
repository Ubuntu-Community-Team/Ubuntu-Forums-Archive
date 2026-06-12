---
title: "&quot;Allocate drive space&quot; blank"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by goodboyCerberus on 2010-10-10
Hi folks, I've been dual booting into Ubuntu and Windows 7 for a while. I broke my 10.4 installation trying to "update-manager -d" to the 10.10 beta. I just burned the ISO for my system, booted from CD, and used GParted to erase the bad installation. 

I want to install Ubuntu 10.10 here (vanilla, no screwing around with a separate /home partition):

[IMG]http://b.imagehost.org/0990/Screenshot-dev-sda_GParted.png[/IMG]

I go to install and get this at the "Allocate drive space" window:

[IMG]http://b.imagehost.org/0176/Screenshot-Install.png[/IMG]

What am I doing wrong and how do I fix it?

Thank you.

---

### Post by goodboyCerberus on 2010-10-10
[QUOTE="goodboyCerberus"]I've been dual booting ... used GParted to erase the bad installation[/QUOTE]

#-o **Don't do this.** Now I deleted grub and can't go back into Windows. What a stupid mistake...

Also, [EMR]("http://ubuntuforums.org/showthread.php?t=1591685") and I seem to be having a similar problem.

sudo fdisk -lu:
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848  1021460894   510627023+   7  HPFS/NTFS
/dev/sda3      1226260480  1249996799    11868160    7  HPFS/NTFS
```

---

### Post by srs5694 on 2010-10-10
Your partition table looks OK to me. I'm not sure what the problem is at this point.

---

### Post by goodboyCerberus on 2010-10-10
In the meantime, how do I make Windows bootable again? If I were to restart I would get a black screen and a prompt saying something like: 

That partition does not exist
grub rescue>_

Edit: This is blasphemy, and I intend to re-install, but this is good information:
[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)

---

### Post by Mark Phelps on 2010-10-11
When you were in Win7, did you use the Backup feature to create and burn an Win7 Repair CD?  Don't need to answer that ... no-one does that.

So, go to the link below, download the proper Win7 Repair CD image, burn that to CD, boot from that CD, and run Startup Rpair three times -- yes, that's three times!

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

That should get you back into being able to boot into Win7.

---

### Post by goodboyCerberus on 2010-10-17
Sorry for the delayed response. 

I was able to get back into Windows 7 after using a repair CD. I used wubi, restarted when prompted, and got this:

[IMG]http://b.imagehost.org/0802/1010002103.jpg[/IMG]

Clicking "OK" just brings up the same error message. Should I use GParted on a regular Ubuntu install CD?

---

### Post by goodboyCerberus on 2010-10-23
This solution worked for me!

[http://ubuntuforums.org/showpost.php?p=8225121&postcount=1](http://ubuntuforums.org/showpost.php?p=8225121&postcount=1)

---

