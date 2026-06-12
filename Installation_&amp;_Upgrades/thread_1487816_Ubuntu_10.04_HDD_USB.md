---
title: "Ubuntu 10.04 HDD USB"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by krolikbunny on 2010-05-19
I've installed ubuntu 10.04 on my usb-hdd and grub on usb hdd. i start it with F8 or F12(on some laptops) It works great on my desktop(old comp) and laptop (old Toshiba), it works on my laptop( new Toshiba) in work also, but it doesn't work on some computers. During boot i have unknown file system error and grub rescue. I've tired to boot manually, it didn't work. i think that the problem is BIOS and hdd selection. Is there any chance to fix or replace grub with other bootloader. For any help or hints i would be grateful.

---

### Post by efflandt on 2010-05-19
It may related to the new partition alignment on MB boundaries instead of cylinder boundaries.  That was a problem with my HP desktop with Asus mobo from 2004.  [http://www.ubuntu.com/getubuntu/releasenotes/1004#Partition%20alignment%20changes%20may%20break%20some%20systems](http://www.ubuntu.com/getubuntu/releasenotes/1004#Partition%20alignment%20changes%20may%20break%20some%20systems)

Either 500 GB or 160 GB USB drives (WD Passport) with 64-bit 10.04 LTS would boot fine on 2 different laptops, but not on my desktop (which previously was able to boot 64-bit 9.10 from the 160 GB).  But the error messages before dumping into grub rescue were different.  Error for the large drive was "unknown filesystem" and error for the smaller drive was "file not found".

Strangely grub rescue on the smaller drive could read the directories on my main 200 GB hard drive, but on the USB drive, it could display the contents of /, but contents of **/boot** was a happy face ascii symbol, and **ls (hd0,3)/boot/grub** returned "file not found".

I got the 160 GB drive to boot on the problem desktop by formatting the drive from 9.10 and then using the partman/alignment=cylinder kernel parameter when booting the 10.04 install CD.  So I then installed 64-bit 10.04 LTS to the 200 GB internal drive of the problem desktop, and am running fine from it now.

But why the 500 GB USB drive will not boot is still a mystery.  I formatted and installed it from 10.04 iso on USB (using partman/alignment=cylinder).  grub rescue from the USB drive says "unknown filesystem" for all partitions on the drive.  The same full grub 1.98 on my main drive can **ls** the ntfs partition, but the 10.04 ext3 partition still returns unknown filesystem.  Maybe there is some old Ami BIOS limitation that works for 200 GB, but fails somewhere under 500 GB.

The only thing I have not tried yet is installing to the big drive from the problem PC to see if it implements its own workaround.

---

### Post by krolikbunny on 2010-05-24
Thanku you efflandt for your reply.
I have 500GB hdd Usb and it works fine with Ubuntu on my desktop and my laptop and my laptop at work, but not everywhere ( for example it doesn't work on my desktop at work --- 7 months old comp with 640 MB 3.5 internal hdd---) I hope anyone can help me, bc i've almost have a mobile system on my 2.5 HDD and i would be very happy if it works on every comp.
I think that the solution is in BIOS boot HDD order 
More info about mu usb hdd:
 
(SAMSUNG HM500JI USB Device)
Total size:
465.7 GB
500 107 862 016 Bytes
976 773 168 Sectors
Cylinders:
0xED81(60801)
Heads:
0xFF(255)
Sectors per track:
0x3F(63)
 
Logical Disk (H:)
 
Volume letter:
(H:)
Volume label:
HDD_USB
Type:
Primary
File system:
NTFS
Root entries:
7252
Sectors per boot:
8
Sectors per cluster:
8
 
Serial number:
57DB1100
Partition ID:
0x07 NTFS
NTFS version:
3.01
Total size:
390.6 GB
Used space:
16.9 GB
Free space:
373.6 GB
Activity:
Active
Hidden state:
Not hidden
 
 
 
Extended partition
 
Total size:
75.1 GB
 
 
Logical Disk (*)
 
Volume letter:
(*)
Volume label:
[No label]
Type:
Logical
File system:
Linux Ext3
Sectors per boot:
2
Sectors per cluster:
8
 
Serial number:
0
Partition ID:
0x83 Linux Native
Total size:
72 GB
Used space:
10.4 GB
Free space:
61.6 GB
Activity:
Inactive
Hidden state:
Not hidden
 
 
 
 
9641Logical Disk (*)
 
Volume letter:
(*)
Volume label:
[No label]
Type:
Logical
File system:
Linux Swap2
Sectors per boot:
8
Sectors per cluster:
8
 
Serial number:
0
Partition ID:
0x82 Linux swap
Total size:
3.1 GB
Used space:
7 KB
Free space:
3.1 GB
Activity:
Inactive
Hidden state:
Not hidden

---

### Post by krolikbunny on 2010-06-28
I've already found a solution. I've installed ubuntu 10.04 on comp that had grub rescue error before. Everything works great now on every comp. I have a mobile usb system :)

---

### Post by ssuuddoo on 2011-05-05
hmmm. I do not fully understand UR solution.
have the...Grub Rescue> Unknown filesystem... problem too
and have installed the system on the comp with this error, but now it boots well only on some comps.
the sys is 11.04

thnx

---

### Post by K1251 on 2011-05-05
It won't let me delete my post. So yeah. Moved it to new thread.

---

### Post by krolikbunny on 2011-05-17
I had this issue again with 11.04 but when i quit decryption of home folder all problems were gone. So i use trucrypt now.
So i think ther eis a problem when you decrypt your home folder during instalation, then u cant go with your pendrive/ hdd .Try it without decryption

---

