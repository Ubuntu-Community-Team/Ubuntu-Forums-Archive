---
title: "new hard drive and Windows XP won't start"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by Knacker on 2008-04-06
I recently upgraded my hard drive. I used Acronis True Image to copy a disk image, including all partitions (for dual boot, XP + gutsy) to the new HDD and then just replaced the old one with this new disk. 

Everything worked without a hitch for Ubuntu :D. My problem is that I can't boot Windows XP. When I select Windows XP from the grub menu at start up, it hangs on a screen saying "Starting up...". I've looked through forums and googled around and I've got some ideas, but no sure solution and I'd rather not make a mess of things (again!) trying to free-style things. 

The problem, as far as I can tell, is in the final line of the output for "sudo fdisk -l":

[INDENT]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3df90ffd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4950    39760843+   7  HPFS/NTFS
/dev/sda2   *       18729       19457     5855692+  12  Compaq diagnostics
/dev/sda3            4951       18019   104976742+  83  Linux
/dev/sda4           18020       18728     5695042+  82  Linux swap / Solaris

Partition table entries are not in disk orde[/INDENT]

Is this "Partition table entries not in disk order" my problem? If so, how do I fix it?Any ideas? I'm really new and really grateful for any help! 

In case it's useful, here's what the relevant part of my /boot/grub/menu.lst looks like: 

[INDENT]
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4fd87f34-6f09-4820-a3a3-ca52a20cbd1a ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4fd87f34-6f09-4820-a3a3-ca52a20cbd1a ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1
[/INDENT]

---

### Post by Belak on 2008-04-07
I'm not really sure how to fix this. Here's my own 2 Cents, though.
I thought it was easier to back up just the important data and just do a fresh install of Windows XP. I tried this too... almost the same method too and it didn't work. I have absolutely no idea why it wouldn't work.

You might try changing the root (hd0,0) in your menu.lst file to rootnoverify (hd0,0)

Also, just because, I'd change the boot partition to your linux partition.

IDK if any of those will work, but the first one really is the only one that has a chance of changing anything.

---

### Post by Knacker on 2008-04-07
Thanks for your help. 
I can't reinstall windows... I never got an install disk, only pre-installed. 

I'll try doing what you suggest, but I wish someone could explain what it is that's going on. It seems like this would be a pretty common problem/question. It seems like the "Partition table entries are not in disk order" thing is the problem, but it doesn't make sense to me how this is a problem with the grub menu.lst. 
Not because I really understand these things, but just because it sounds like it's a partitioning problem... 

Can someone make sense of this and maybe point me in the right direction...?

Thanks again, Belak!

---

### Post by Herman on 2008-04-07
It's perfectly normal for the partitions not to be in disk order.
The fdisk output for the majority of computers will say that.

Your fdisk output and /boot/grub/menu.lst look okay to me.

It seems to be some kind of acronis problem or a Windows problem. 

The best suggestion I can think of right now is to try going to the following site, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm") Download a boot CD or USB or floppy and try following the instructions in that web page.
Those CD images or USB or floppy disks contain their own copy of NTLDR, NTdetect.com and a generic boot.ini file.
That means you're bypassing your MBR, boot sector, the boot loader and boot.ini, so if one of those boot discs doesn't boot your Windows for you I don't know what will.

---

