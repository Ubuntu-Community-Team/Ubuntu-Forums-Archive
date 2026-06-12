---
title: "Dual-Boot Problem"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by kleft on 2008-03-18
First off, i'm new to Linux and don't know a huge amount about it to say the least.Ok here's my problem.

I have a Windows installation and just set up Ubuntu as a second partition. It worked fine but when I loaded Windows up, I realised I had an empty active partition. I went to delete it because I was going to reattach it to my windows partition but i'm fairly certain that when I did, it deleted the boot section of my Linux partition. Now when I boot, my windows doesn't load and I get a "Grub Error 17" message.

With the recovery console from the windows, I can see my windows partition is fine and I even made a new boot section for it but because my hdd thinks the Linux installation is most first, I can't get past this message. I could just reinstall windows and then ubuntu again but I don't want to do that unless I have to. Any ideas? Is there an automated repair function on the ubuntu installation disc? I have both the windows disc and the ubuntu disc.

---

### Post by Pumalite on 2008-03-18
Who owned the boot loader; Windows or Ubuntu? Here is a link for you to get informed of the possibilities:
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by kleft on 2008-03-18
I can only assume Ubuntu owned the boot loader because it was the primary os when loading and now i can't load windows without the ubuntu boot section. I really amn't sure though cause I've reinstalled a few systems and they have either been just windows or just ubuntu, not dual boots.

---

### Post by kleft on 2008-03-18
In the partition editor, on the LiveCD, it's telling me my entire hdd is unallocated but i can view my windows files through the windows recovery cd. I have no idea why. Is there anyway I can make a new boot section for ubuntu from the LiveCD? I seem to be able to see my files through the File Browser whilst on a LiveCD session and it sees them as two separate hdd's.

---

### Post by logos34 on 2008-03-19
> **kleft said:**
> In the partition editor, on the LiveCD, it's telling me my entire hdd is unallocated but i can view my windows files through the windows recovery cd. I have no idea why. Is there anyway I can make a new boot section for ubuntu from the LiveCD? I seem to be able to see my files through the File Browser whilst on a LiveCD session and it sees them as two separate hdd's.

Your partition table is messed up.

So, gparted says the hard disk is blank, but nautilus shows the partitions.  What about the installer?  Try starting the installation, but if it doesn't see the partitions, exit.  Restore the windows bootloader (XP CD>recovery console>**fixmbr**) and then use the XP disk utility to delete the other partition.  Boot up the ubuntu cd again--hopefully this time it will see windows and the empty space.  If not you could try TestDisk to fix the partition table.

Edit: if necessary use gparted on the ubuntu cd to flag the windows partition as active/boot.

---

### Post by Shazaam on 2008-03-19
Since I have run across the unallocated space problem before running the Ubuntu livecd DO NOT modify anything at this time with gparted (while running the livecd). Reboot the machine first (using the Ubuntu livecd again) and see if the same problem occurs.
The reason I say this is I had the same problem. Booted the livecd, ran gparted and it reported that the whole hard drive was unallocated space. 7 distros gone according to gparted. Rebooted the pc with the livecd in and opened gparted again. Everything was where it should be. I've run across this several times (including using the gparted livecd).

---

### Post by kleft on 2008-03-20
Thanks for the answers but I don't know all that much about partitioning so I just used the LiveCD to copy all my Windows files onto an ext HDD and then just reinstalled Windows and then Ubuntu.

---

