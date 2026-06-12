---
title: "USB drive install failed"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by gringo loco on 2011-07-09
After years of suffering through progressively more frustrating versions of Windows, a friend of mine gave me a USB stick with a bootable copy of Ubuntu installed in one of the partitions. It worked great and I have been able to use Ubuntu in all sorts of computers including most Internet cafes simply by booting from USB.
Unfortunately that stick has developed a problem and no longer works. I found instructions to make a new one but have not been able to actually do it and I don't know why, I hope someone can help me.

I am trying to do it using my netbook with Ubuntu 10.04 OS. and a new 16 gig Kingston USB stick. I used gparted to partition the USB drive and formatted 4gig ext3/4 and 9gig fat32, leaving the rest as linux swap. I then downloaded "ubuntu-10.04.2-alternate-i386.iso" as a torrent and installed it on the ext4 partition using UNetBootin and followed the instructions (I think) all the files seemed to load but when I tried to reboot my netbook from USB it said the stick had no OS. I then tried to install it on the fat32 partition using the "start-up disk creator" and all I could get is a small window that said "installation failed".

Any suggestions would be helpful, I know it can be done and I'm probably missing something simple but I'm new to this type of exercise and eager to learn because I've finally found a OS that I really like using and that doesn't drive me crazy by acting like it is capable of thinking for me HAHA. LOVE UBUNTU and don't know why anyone would actually choose to use MS products but oh well each to their own.

Look forward to ideas

---

### Post by mörgæs on 2011-07-09
Hi, welcome to the fora.

Can you create a bootable USB if you delete everything on it (no partitioning) and simply let Unetbootin do the work?

Why did you choose the alternate? It is good for installing, but it does not run a live session.

---

### Post by oldfred on 2011-07-09
With a 16GB flash you can do a full install. The standard USB creators assume smaller 4GB or less and usually reformat entire flash and just install a liveCD version. If you just want a liveCD/USB version I would just buy a 4 or 2GB flash drive.

A full install is not an installer to a hard drive or another system.

Pros & cons of persistent install over direct install to flashdrives 
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

---

### Post by gringo loco on 2011-07-12
Thanks for the suggestions. I'm using 3rd world intermittent internet connections will take a few more days to check out the links and info, then try again to get my usb drive operating. I'll let you know how it goes. In the meantime I will continue to enjoy Ubuntu on my desktop and netbook.

---

### Post by gringo loco on 2011-07-15
Success. I purchased a couple of new pny memory devices and used UNetbootin to load ubuntu from "ubuntu-10.04.2-desktop-i386.iso" (torrent download) onto a 4 gig flash drive and booted the computer from this. The next step involved mounting another USB device (4gig cellphone memory in USB adapter)and doing a complete install onto that. It all went smoothly and the result is that I now have a full Ubuntu OS that I can keep in my wallet (the USB adapter is on my key ring) and use it to operate any computer that boots from USB. I still have a little tweaking to do related to wireless card drivers but that is another issue. Thanks for all your help and it's great to be part of the growing Ubuntu community.

---

