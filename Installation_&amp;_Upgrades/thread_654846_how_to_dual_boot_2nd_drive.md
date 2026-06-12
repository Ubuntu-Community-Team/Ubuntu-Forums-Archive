---
title: "how to dual boot 2nd drive"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by wayneharper on 2007-12-31
I installed a 2nd sata drive.
I disconnected the 1st drive & installed Ubuntu on the 2nd drive  as I didnt want it to make ANY changes to my existing windows xp installation.
It can only boot from one hard drive so I cant boot to linux unless the 1st drive is disconnected.
how can I fix it so I can boot to either OS ?
(I tried follwing the instructions about bootpart.exe but it didnt work)
Thanks, Wayne

---

### Post by Pumalite on 2007-12-31
You can add ubuntu to the windows boot loader:

Boot from the LiveD.

Step 1) Install Ubuntu. On the last screen click on the "advanced" button and replace (hd0) by /dev/sda3. (Here you need to replace sda3 by whatever partition Ubuntu is on)

Don't reboot immediately. Instead stay on the LiveCD.

Step 2) Mount your Windows partition:

Code:

sudo mount  -t ntfs-3g  /dev/sda2 /windows

(Here replace sda2 by whatever partition Windows is on)

Step 3) Copy the first sector of the Ubuntu partition to a file on the Windows partition:

Code:

sudo dd if=/dev/sda3 of=/windows/ubuntu.bin bs=512 count=1

(Be very careful when using "dd". Info on dd)

Step 4) Add ubuntu to the windows boot loader:

Open "boot.ini" from the Windows partition via
Code:

sudo gedit /windows/boot.ini

Add this line to the end of the file:
c:\ubuntu.bin="Ubuntu"

Save the file.

Reboot and you get should get a menu with a Windows and Ubuntu choice.
__________________

---

### Post by wayneharper on 2007-12-31
is there some way to do this without re-installing Ubuntu?

---

### Post by Pumalite on 2007-12-31
Those are general guidelines. If you have Ubuntu installed, you can skip that. What you need to know is what partition is Ubuntu at.

---

### Post by wayneharper on 2007-12-31
how can I tell what partition ubuntu is installed on? I mean the sdb1 or whatever

---

### Post by Pumalite on 2007-12-31
Boot your Live CD and from the Terminal, post:
sudo fdisk -lu

---

### Post by wayneharper on 2008-01-01
***********Here is the ouput of the fdisk command:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       64259       32098+  de  Dell Utility
/dev/sda2   *       64260   156232124    78083932+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x48c6e44c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    12289724     6144831   83  Linux
/dev/sdb2       309620745   312576704     1477980    5  Extended
/dev/sdb3        12289725   309620744   148665510    b  W95 FAT32
/dev/sdb5       309620808   312576704     1477948+  82  Linux swap / Solaris

Partition table entries are not in disk order
***************end of fdisk ouput**************

when I do this:
sudo dd if=/dev/sdb1 of=ubuntu.bin bs=512 count=1

then I view the fille ubuntu.bin in a hex editor, it has nothing but nulls , 512 bytes

---

### Post by Pumalite on 2008-01-01
sudo dd if=/dev/sdb1 of=/windows/ubuntu.bin bs=512 count=1

---

### Post by logos34 on 2008-01-01
Here's what I get from mine:

> 00000000   EB 48 90 00  00 00 00 00  00 00 00 00  00 00 00 00  .H..............
00000010   00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
00000020   00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
00000030   00 00 00 00  00 00 00 00  00 00 00 00  00 00 03 02  ................
00000040   FF 00 00 80  0C 14 B0 0C  00 08 FA 90  90 F6 C2 80  ................
00000050   75 02 B2 80  EA 59 7C 00  00 31 C0 8E  D8 8E D0 BC  u....Y|..1......
00000060   00 20 FB A0  40 7C 3C FF  74 02 88 C2  52 BE 7F 7D  . ..@|<.t...R..}
00000070   E8 34 01 F6  C2 80 74 54  B4 41 BB AA  55 CD 13 5A  .4....tT.A..U..Z
00000080   52 72 49 81  FB 55 AA 75  43 A0 41 7C  84 C0 75 05  RrI..U.uC.A|..u.
00000090   83 E1 01 74  37 66 8B 4C  10 BE 05 7C  C6 44 FF 01  ...t7f.L...|.D..
000000A0   66 8B 1E 44  7C C7 04 10  00 C7 44 02  01 00 66 89  f..D|.....D...f.
000000B0   5C 08 C7 44  06 00 70 66  31 C0 89 44  04 66 89 44  \..D..pf1..D.f.D
000000C0   0C B4 42 CD  13 72 05 BB  00 70 EB 7D  B4 08 CD 13  ..B..r...p.}....
000000D0   73 0A F6 C2  80 0F 84 EA  00 E9 8D 00  BE 05 7C C6  s.............|.
000000E0   44 FF 00 66  31 C0 88 F0  40 66 89 44  04 31 D2 88  D..f1...@f.D.1..
000000F0   CA C1 E2 02  88 E8 88 F4  40 89 44 08  31 C0 88 D0  ........@.D.1...
00000100   C0 E8 02 66  89 04 66 A1  44 7C 66 31  D2 66 F7 34  ...f..f.D|f1.f.4
00000110   88 54 0A 66  31 D2 66 F7  74 04 88 54  0B 89 44 0C  .T.f1.f.t..T..D.
00000120   3B 44 08 7D  3C 8A 54 0D  C0 E2 06 8A  4C 0A FE C1  ;D.}<.T.....L...
00000130   08 D1 8A 6C  0C 5A 8A 74  0B BB 00 70  8E C3 31 DB  ...l.Z.t...p..1.
00000140   B8 01 02 CD  13 72 2A 8C  C3 8E 06 48  7C 60 1E B9  .....r*....H|`..
00000150   00 01 8E DB  31 F6 31 FF  FC F3 A5 1F  61 FF 26 42  ....1.1.....a.&B
00000160   7C BE 85 7D  E8 40 00 EB  0E BE 8A 7D  E8 38 00 EB  |..}.@.....}.8..
-%%  ubuntu.bin       --0x0/0x200----------------------------------------------

Frankly I don't know why you didn't try doing it the other way round first--i.e. adding a windows entry to bottom of ubuntu menu.lst:

gksudo gedit /boot/grub/menu.lst

> title           Windows XP
root            (hd1,1)
savedefault
makeactive
map            (hd0) (hd1)
map            (hd1) (hd0)
chainloader     +1


add windows drive to /boot/grub/device.map:

> (hd0) /dev/sdb
**(hd1) /dev/sda**

---

### Post by wayneharper on 2008-01-01
(by the way thanks for taking the time to reply to my posts)

>Frankly I don't know why you didn't try doing it the other way round first

unfortunately windows is my bread & butter right now & I cant afford to risk messing up my installation.
also I can only boot to the xp drive unless I disable it, or switch them round which I dont want to do.

I cant understand why the ubuntu.bin file is all nulls.

---

### Post by logos34 on 2008-01-01
> **wayneharper said:**
> unfortunately windows is my bread & butter right now & I cant afford to risk messing up my installation.
also I can only boot to the xp drive unless I disable it, or switch them round which I dont want to do.

I cant understand why the ubuntu.bin file is all nulls.

adding xp to menu.lst won't alter/mess up your installation or change one iota on windows disk.

So, you can't set the ubuntu drive first, connect the xp drive in second place, and boot to grub that way? (adding the xp entry will give you a choice of OSs on grub menu screen)

maybe pumalite has some ideas about the nulls.

---

### Post by Pumalite on 2008-01-01
Even though I helped you with the other configuration, I agree with logos34 that Grub is the best boot loader around. Period. The advise he gave you is right on the mark too.

---

### Post by logos34 on 2008-01-01
> **wayneharper said:**
> I cant understand why the ubuntu.bin file is all nulls.

As far as that goes, it just occurred to me that perhaps you don't have grub installed to the bootsector of the linux root partition:

**sudo grub-install /dev/sdb1**

Now the dd command should make a proper .bin file.  Just for future reference.

---

### Post by wayneharper on 2008-01-02
when I do that it says:

/dev/sdb1 does not have any corresponding BIOS drive.

---

### Post by logos34 on 2008-01-02
if the windows drive isn't hooked up it will be /dev/sda1

check with 

sudo fdisk -l

otherwise try 

> sudo grub
> find /boot/grub/stage1
(should show 'hd0,0'.  Enter output in next command)
> root (hd0,0)
> setup (hd0,0)

But the point is you should probably try to use grub as your bootloader instead.

---

### Post by wayneharper on 2008-01-03
I got this working. Re-installed Ubuntu with boot loader to hd1. Shouldnt have had 1st drive disconnected the first time.    also "ubutu.bin" file that dd created didnt work, had to use bootpart.exe.
Thanks, Wayne

---

### Post by logos34 on 2008-01-03
> **wayneharper said:**
> I got this working. Re-installed Ubuntu with boot loader to hd1. Shouldnt have had 1st drive disconnected the first time.    also "ubutu.bin" file that dd created didnt work, had to use bootpart.exe.
Thanks, Wayne

well I'm still confused as to the problem (thought you said the machine would only boot linux with windows drive disconnected) but, hey, whatever works.  good luck and enjoy ubuntu

---

