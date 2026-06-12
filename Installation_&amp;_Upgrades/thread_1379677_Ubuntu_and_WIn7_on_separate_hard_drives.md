---
title: "Ubuntu and WIn7 on separate hard drives?"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by gilch on 2010-01-12
I have two 300gb hard drives and two 1TB drives, (plus external 2GB) so space is not a problem.

I have installed Windows 7 on the first one.

Is it better to make room on this one drive, or to install Ubuntu on a separate 300gb drive? Will it create problems if they are on separate drives?

Should the two 1TB ones be formatted as ext3 or ntfs? What would be best? 

My data is mostly music and language and woodworking related stuff: almost ready to start filing the second 1TB drive the first one being full. Games are not a major activity for me.

Thanks in advance.

Gilles

---

### Post by kunks112 on 2010-01-12
I had a triple boot system. All three separate hard drives (500 GB each). Ubuntu, Vista, W7 (RC).

I kept most of my files on a 4th 1.5 TB NTFS formatted drive. From all three OS's I was able to access the information on the 1.5 TB.

Hope this helps in anyway.

---

### Post by rcorbish on 2010-01-12
I would keep them separate. When I installed W7 after an ubuntu install - I had to disable the other disk in the BIOS before windows would play nice. It seems W7 looks for any bootable partition and refuses to install unless it's installed there.

If you have to reinstall W7 - you may need to do it as though that's the only OS there. You can put the real OS back later - grub will find windows and add it to the menu automatically

---

### Post by tatmark1 on 2010-01-12
I had vista and ubuntu installed on separate drives. I uplugged the ubuntu drive and upgrade vista to windows 7. plugged ubuntu back in but now i can only boot windows. Im not sure how to get back to dual booting. please help

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdefd3c49

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       60802   488282112    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00023388

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29272   235127308+  83  Linux
/dev/sdb2           29273       30401     9068692+   5  Extended
/dev/sdb5           29273       30401     9068661   82  Linux swap / Solaris

---

### Post by rcorbish on 2010-01-12
You'll have to go into the BIOS to set a different boot order for the hard disks. Alternatively (maybe) you can hit ESC during startup to choose a boot device (depends on your computer).

---

### Post by tatmark1 on 2010-01-12
I previously was using grub and would like to get that working again

---

### Post by tatmark1 on 2010-01-12
ok i changed the boot order in bios, was able to bring grub up but it still has vista on it no 7 . so now im in my ubuntu but how do i get windows 7 on the grub boot list?

---

### Post by tatmark1 on 2010-01-13
help?

---

### Post by tatmark1 on 2010-01-13
please

---

### Post by rcorbish on 2010-01-13
You can try to rebuild grub2 boot list...

**sudo update-grub**

Should find the Windows 7

---

### Post by gilch on 2010-01-16
Since I was the originator of this thread, I would like to thank my first responder. I followed his/her advice, and after a couple of errors on my part, everything worked fine, and I now have dual boot. Thank you a whole lot.
Gilles

---

