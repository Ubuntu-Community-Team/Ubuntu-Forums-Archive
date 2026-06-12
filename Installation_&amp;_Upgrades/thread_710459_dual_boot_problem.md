---
title: "dual boot problem"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by ac3raven on 2008-02-28
I need to dual boot XP and Ubuntu, but I have no idea how to even do this.  I've seen tons of tutorials and I've tried this 3 times already, but I can't seem to get it right.  Here's my situation:

I have a 2 hard drive raid 0 array with XP installed on it.  This is my primary partition, a few months ago I tried to dual boot Ubuntu and XP on this raid array, but I failed miserably so I gave up.  Now, I have a 3rd hard drive, a 320gb SATA II, that's independent of the raid array.  I figured it would be much easier to dual boot like this because I figured I would not have to deal with dmraid and whatnot.  I followed [https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

I installed Ubuntu on the 320gb, it asked me if I wanted to keep using the live cd, I said yes.  So I can't edit the menu.lst like I need to, or even back it up.  here's my terminal when I try to back up the menu.lst:

ubuntu@ubuntu:~$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkp
cp: cannot stat `/boot/grub/menu.lst': No such file or directory
ubuntu@ubuntu:~$ 

here's my terminal when I do fdisk:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8aeb8ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312576673+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c91043d

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000473fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38157   306496071   83  Linux
/dev/sdc2           38158       38913     6072570    5  Extended
/dev/sdc5           38158       38913     6072538+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

I see here that the hard drive I want is sdc, and it shows that I have installed linux on it.

Here's my terminal when I try to edit the menu.lst:

ubuntu@ubuntu:~$ sudo gedit /boot/grub/menu.lst

that opens a blank text document named menu.lst.  Isn't it suppose to open the actual menu.lst?

I tried opening via gui, and I could, but because I'm on a live cd I can't save the changes I make to it.  But I mounted the 320gb, and installed linux on it, and the menu.lst is in the /boot/grub folder of the the 320gb mounted volume, so I don't understand why I can't edit it.  But I really can't get passed that.  I tried just installing it, then removing the live cd and rebooting, but as expected, it gave me error 21.  If some could provide for me an actually DETAILED tutorial on how to do this, then I might not screw it up like the last 3 times I've tried this.  Basically, I need to know why I can't back up the menu.lst, why I can't edit it, and why won't grub leave my raid array alone?  PLEASE HELP!

---

### Post by poofyyoda on 2008-02-28
when your'e doing 
> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkp
sudo gedit /boot/grub/menu.lst
these, the reason its not working is that, the live session is the filesystem.  
You have to first change path to your harddrive:

```
cd /media/disk#
```

---

### Post by ac3raven on 2008-02-28
ubuntu@ubuntu:~$ cd /media/disk
ubuntu@ubuntu:/media/disk$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkp
cp: cannot stat `/boot/grub/menu.lst': No such file or directory
ubuntu@ubuntu:/media/disk$ 


same result.

---

### Post by poofyyoda on 2008-02-28
Remove the first forward slash, in front of 'boot'.  Also on the copy path.
What its doing is going back to the filesystem when you use /boot/grub/....

so do 

```
sudo cp boot/grub/menu.lst boot/grub/menu.lst.bkp
```

or just do

```
sudo cp /media/disk/boot/grub/menu.lst /media/disk/boot/grub/menu.lst.bkp
```

---

### Post by ac3raven on 2008-02-28
okay, it seems to be working now.  The linked tutorial above says:

If your Windows is on a second SATA you have to use sd1 instead of hd1, I think. The second line of the map command is just so your Ubuntu hard drive will be recognizeable on Windows.

Since my raid array ios using both sata 1 and 2, should I be worried about this?

---

### Post by poofyyoda on 2008-02-28
I think the tutorial your'e following, is for if you installed xp and ubuntu seperately.  It sounds like you've installed ubuntu while the xp drive is in?
If yes, then the grub boot loader should automatically detect it.

---

### Post by ac3raven on 2008-02-28
that is the case, I just need to make sure that, because it's a raid array using sata 1 and 2, would their be any issue with this?

title           Windows XP Home
root            (hd1,0)
savedefault
makeactive
chainloader     +1
map (hd0) (hd1)
map (hd1) (hd0)

---

### Post by ac3raven on 2008-02-28
okay, now I edited the menu.lst but I can't save it.  It's telling me that I do not have permission, I presume this has something to do with the live cd, so how do I save it?

---

### Post by ac3raven on 2008-02-28
here's the bottom portion of my menu.lst, absent the proper formatting.


## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=aea8658f-194f-4603-a428-5cb65b4f5ccc ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=aea8658f-194f-4603-a428-5cb65b4f5ccc ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

title           Windows XP Home
root            (hd1,0)
savedefault
makeactive
chainloader     +1
map (hd0) (hd1)
map (hd1) (hd0)


### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by poofyyoda on 2008-02-28
The live session, prevents modifying, unless you use root terminal:
```

gksu /usr/bin/x-terminal-emulator
```

---

### Post by ac3raven on 2008-02-28
okay, I did it.  But I'm still getting error 21.  I tried adjusting the boot device priority, putting my 320gb in front, but that just resulted in a black screen with a blinking cursor.  Why am I still getting error 21?

---

### Post by froy02 on 2008-02-28
This what I see in your setup:
1. You have 3 hard drives but the first 2 are configured raid (technically 1 drive)
2. Your windows installation is on the first hard drive.
3. Your linux istallation in on the 3rd hard drive but technically the 2nd.

So then your windows entry in the menu.lst should be as follows with no mapping: 

title Windows XP Home
root (hd0,0)
savedefault
makeactive
chainloader +1

As for the linux try this:

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=aea8658f-194f-4603-a428-5cb65b4f5ccc ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

These entries are based on what you supplied from your fdisk output and the menu.lst that you published.

NOTE:
When you boot with live cd use the nautilus file browser as root by typing the command 'gksu nautilus' in a terminal.  This would give you a root access including when you click on a text file, like menu.lst , gedit will open it for you where you can save it.  You can copy any file with Nautilus opened with gksu including system files. Just be careful with it.

---

### Post by ac3raven on 2008-02-29
alright, I'll try that when I get a chance, and if (or when) something goes wrong, I'll be back.

---

### Post by ac3raven on 2008-03-04
Still getting error 21.

---

### Post by ac3raven on 2008-03-04
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=02284fd3-0d65-43df-a4cf-f97e01967171 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=02284fd3-0d65-43df-a4cf-f97e01967171 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

title 		Windows XP Home
root 		(hd0,0)
savedefault
makeactive
chainloader 	+1

---

### Post by ac3raven on 2008-03-04
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc


this is my device.map, I tried also putting hd2,0 as the root for the linux hard drive considering that sdc is my 320 on the fdisk.  Still didn't work.

---

### Post by ac3raven on 2008-03-04
When I install ubuntu, I just select guided-use entire disk, and select the 320, should I try something else?

---

