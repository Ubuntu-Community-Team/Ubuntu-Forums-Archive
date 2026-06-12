---
title: "A tiny favour please..."
date: 2006-03-10
forum: Installation &amp; Upgrades
---

### Post by ubuntu-mike022465 on 2006-03-10
I hope you folks can help me, I'm looking to edit (without having to reinstall) grub so that it can see my other hd that has fc4 on it so that I can have the option to boot into it from the grub menu in Ubuntu.  ](*,)

Would anyone be so kind as to post their /boot/grub/menu.lst on here in the forum, where you have 2 separate hard drives, one with Ubuntu on it, and the other with whatever other distro you have. (Note: I am not infecting my desktop unit with a windows hard drive! It is a Linux Only desktop!) [-o<

I have googled, and searched these forums til my *** hurts, and I've had no success.  :-({|=

Your kind indulgence would be greatly appreciated.  

Thanks

M.

Additionally, the two drives, the master being my ubuntu drive, and the fc4 being the slave drive, are on the same IDE cable.

---

### Post by aysiu on 2006-03-10
It's better to use your own Grub than someone else's.

If I'm understanding the situation correctly, you have Fedora installed on one drive and Ubuntu installed on the other with Ubuntu's Grub on the MBR (Master Boot Record), and there's no Grub entry for Fedora?

Your best bet is to mount the Fedora partition and look at Fedora's Grub menu and copy that entry to Ubuntu's /boot/grub/menu.lst

Do you know how to mount the Fedora partition in Ubuntu?
Do you know how to edit the /boot/grub/menu.lst?

---

### Post by ubuntu-mike022465 on 2006-03-10
Here's my fdisk -l

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1216     9767488+  83  Linux
/dev/hda2   *        1217        9384    65609460   83  Linux
/dev/hda3            9385        9733     2803342+   5  Extended
/dev/hda5            9385        9733     2803311   82  Linux swap / Solaris

Disk /dev/hdb: 17.0 GB, 17020329984 bytes
255 heads, 63 sectors/track, 2069 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14        2069    16514820   8e  Linux LVM



Here's my menu.lst

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-k7 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda2 vga=795 ro quiet splash acpi=off noapic nolapic
initrd		/boot/initrd.img-2.6.12-10-k7
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12_AthlonXP 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-2.6.12athlonxp root=/dev/hda2 vga=795 ro quiet splash acpi=off noapic nolapic 
initrd		/boot/initrd.img-2.6.12-2.6.12athlonxp
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

##Additional Operating Systems
##


title		Fedora Core 4 <== no brainer here :P
root		(hd1,0) <== common sense??
kernel		/vmlinuz-2.6.15-1.1834_FC4 ro root=dev/VolGroup00/LogVol00 rhgb quiet <== pulled directly from the grub menu in FC4
initrd		/initrd-2.6.15-1.1834_FC4.img <== pulled directly from the grub menu in FC4



And regarding:
"Do you know how to mount the Fedora partition in Ubuntu?
Do you know how to edit the /boot/grub/menu.lst?"

I can figure out the first question, by editing my fstab if necessary, and yes to the second question.  \\:D/

---

### Post by aysiu on 2006-03-10
I don't know much about LVM, but I'm going to assume your Fedora installation is on /dev/hdb1 and that it's an Ext3 partition. If it's actually on /dev/hdb2 or Reiserfs, modify these instructions accordingly.

```
sudo mkdir /tmp/fedora
sudo mount -t ext3 /dev/hdb1 /tmp/fedora
cd /tmp/fedora/boot
ls
cd grub
ls
cat menu.lst
``` Can you post the output of all of those commands?

---

### Post by ubuntu-mike022465 on 2006-03-10
mike@ubuntu:~$ sudo mkdir /tmp/fedora
Password:
mike@ubuntu:~$ sudo mount -t ext3 /dev/hdb1 /tmp/fedora
mike@ubuntu:~$ cd /tmp/fedora/boot
bash: cd: /tmp/fedora/boot: No such file or directory
mike@ubuntu:~$ cd /tmp/fedora
mike@ubuntu:/tmp/fedora$ ls
config-2.6.11-1.1369_FC4      lost+found
config-2.6.13-1.1532_FC4      System.map-2.6.11-1.1369_FC4
config-2.6.14-1.1637_FC4      System.map-2.6.13-1.1532_FC4
config-2.6.15-1.1831_FC4      System.map-2.6.14-1.1637_FC4
grub                          System.map-2.6.15-1.1831_FC4
initrd-2.6.11-1.1369_FC4.img  vmlinuz-2.6.11-1.1369_FC4
initrd-2.6.13-1.1532_FC4.img  vmlinuz-2.6.13-1.1532_FC4
initrd-2.6.14-1.1637_FC4.img  vmlinuz-2.6.14-1.1637_FC4
initrd-2.6.15-1.1831_FC4.img  vmlinuz-2.6.15-1.1831_FC4
mike@ubuntu:/tmp/fedora$ cd grub
mike@ubuntu:/tmp/fedora/grub$ ls
device.map     grub.conf         minix_stage1_5     stage2
e2fs_stage1_5  iso9660_stage1_5  reiserfs_stage1_5  ufs2_stage1_5
fat_stage1_5   jfs_stage1_5      splash.xpm.gz      vstafs_stage1_5
ffs_stage1_5   menu.lst          stage1             xfs_stage1_5
mike@ubuntu:/tmp/fedora/grub$ cat menu.lst
cat: menu.lst: Permission denied
mike@ubuntu:/tmp/fedora/grub$ sudo cat menu.lst
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/hda
default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title Fedora Core (2.6.15-1.1831_FC4)
        root (hd0,0)
        kernel /vmlinuz-2.6.15-1.1831_FC4 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
        initrd /initrd-2.6.15-1.1831_FC4.img
title Fedora Core (2.6.14-1.1637_FC4)
        root (hd0,0)
        kernel /vmlinuz-2.6.14-1.1637_FC4 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
        initrd /initrd-2.6.14-1.1637_FC4.img
title Fedora Core (2.6.13-1.1532_FC4)
        root (hd0,0)
        kernel /vmlinuz-2.6.13-1.1532_FC4 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
        initrd /initrd-2.6.13-1.1532_FC4.img
title Fedora Core (2.6.11-1.1369_FC4)
        root (hd0,0)
        kernel /vmlinuz-2.6.11-1.1369_FC4 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
        initrd /initrd-2.6.11-1.1369_FC4.img
mike@ubuntu:/tmp/fedora/grub$

Thar ya be, laddy.

---

### Post by aysiu on 2006-03-10
```
title Fedora Core (2.6.15-1.1831_FC4)
**root (hd1,0)**
kernel /vmlinuz-2.6.15-1.1831_FC4 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
initrd /initrd-2.6.15-1.1831_FC4.img
``` So you already knew to change the bolded part to *(hd1,0)*, but there's got to be some adjustment, too, with the *VolGroup00/LogVol00* part.

I don't know how LVM works, exactly.
My intuition says *this* might work:
```
title Fedora Core (2.6.15-1.1831_FC4)
root (hd1,0)
kernel /vmlinuz-2.6.15-1.1831_FC4 ro root=/dev/VolGroup10/LogVol10 rhgb quiet
initrd /initrd-2.6.15-1.1831_FC4.img
savedefault
boot
```

**Edit**: Never mind, I have pretty convincing evidence that [won't work](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=volgroup10&btnG=Search). Does anyone know what the deal is with LVM and Grub?

---

### Post by ubuntu-mike022465 on 2006-03-10
K, I got impatient and trashed fc4 but not before I backed up my /home to dvd. :D
I repartitioned the hd and made /boot, /home, and swap primary partitions and the rest part of the extended partition.  No more LVM.

I fiddled with my menu.lst in ubuntu and tried a few times and got as far as

mount: error 6 mounting ext3
Error opening /dev/console!!!!: 2
error dup2'ing fd of 0 to 0
error dup2'ing fd of 0 to 1
error dup2'ing fd of 0 to 2
switchroot: mount failed: 22
kernel panic - not syncing: Attempted to kill init!

Here's fdisk -l as it is now:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1216     9767488+  83  Linux
/dev/hda2   *        1217        9384    65609460   83  Linux
/dev/hda3            9385        9733     2803342+   5  Extended
/dev/hda5            9385        9733     2803311   82  Linux swap / Solaris

Disk /dev/hdb: 17.0 GB, 17020329984 bytes
255 heads, 63 sectors/track, 2069 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14        1033     8193150   83  Linux
/dev/hdb3            1034        1224     1534207+  82  Linux swap / Solaris
/dev/hdb4            1225        2069     6787462+   5  Extended
/dev/hdb5            1225        1377     1228941   83  Linux
/dev/hdb6            1378        1530     1228941   83  Linux
/dev/hdb7            1531        1594      514048+  83  Linux
/dev/hdb8            1595        2069     3815406   83  Linux

And now my menu.lst (only the bottom section)

title		Fedora Core 4
root		(hd1,7)
kernel		/vmlinuz-2.6.11-1.1369_FC4 ro root=Label=/ rhgb quiet
initrd		/initrd-2.6.11-1.1369_FC4.img
boot

Any thoughts?

M.

PS: hdb1 is my /boot
and hdb7 is my /

---

### Post by aysiu on 2006-03-10
[QUOTE=ubuntu-mike022465]```

mount: error 6 mounting ext3
Error opening /dev/console!!!!: 2
error dup2'ing fd of 0 to 0
error dup2'ing fd of 0 to 1
error dup2'ing fd of 0 to 2
switchroot: mount failed: 22
kernel panic - not syncing: Attempted to kill init!
```[/quote] Okay. That sounds bad.

Maybe you need to reinstall Grub:
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

---

### Post by DaBruGo on 2006-03-10
[quote=aysiu]Does anyone know what the deal is with LVM and Grub?[/quote] 
aysiu,

I don't know if this helps, but a friendly forum user gave me this info earlier today ... [http://www.ubuntuforums.org/showthread.php?t=141900]("http://www.ubuntuforums.org/showthread.php?t=141900")


DAVE

---

### Post by ubuntu-mike022465 on 2006-03-11
[QUOTE=aysiu]Okay. That sounds bad.

Maybe you need to reinstall Grub:
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)[/QUOTE]

Am I reinstalling grub for Ubuntu or Fedora?

M.

---

### Post by aysiu on 2006-03-11
[QUOTE=ubuntu-mike022465]Am I reinstalling grub for Fedora or Ubuntu?

M.[/QUOTE] Whichever one is on the Master Boot Record.

---

### Post by ubuntu-mike022465 on 2006-03-11
A little more info might help narrow this down...

I had installed FC4 on a separate occasion where it was the only drive on the IDE channel.

I installed Ubuntu 5.10 separately as well on a single IDE channel with no other hd's on the same cable.

Does that narrow things down a bit?

---

### Post by ubuntu-mike022465 on 2006-03-12
Bump.

---

### Post by ubuntu-mike022465 on 2006-03-12
Bump again... :-D

---

### Post by Lux Perpetua on 2006-03-12
For some reason, this style worked for me and the alternative didn't: ```
root=/dev/mapper/VolGroup00-LogVol00
```I don't really know what the difference is, but it worked (for booting Ubuntu, not Fedora) while the other one didn't. I doubt this will work, but I might as well post it. [/$.02]

---

### Post by Lux Perpetua on 2006-03-12
[QUOTE=ubuntu-mike022465]
Disk /dev/hdb: 17.0 GB, 17020329984 bytes
255 heads, 63 sectors/track, 2069 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14        1033     8193150   83  Linux
/dev/hdb3            1034        1224     1534207+  82  Linux swap / Solaris
/dev/hdb4            1225        2069     6787462+   5  Extended
/dev/hdb5            1225        1377     1228941   83  Linux
/dev/hdb6            1378        1530     1228941   83  Linux
/dev/hdb7            1531        1594      514048+  83  Linux
/dev/hdb8            1595        2069     3815406   83  Linux

And now my menu.lst (only the bottom section)

title		Fedora Core 4
root		(hd1,7)
kernel		/vmlinuz-2.6.11-1.1369_FC4 ro root=Label=/ rhgb quiet
initrd		/initrd-2.6.11-1.1369_FC4.img
boot

Any thoughts?

M.

PS: hdb1 is my /boot
and hdb7 is my /[/QUOTE]
Oh, wait a sec. It looks like my previous post doesn't apply. I don't know what "root=Label=/" means, but I believe that (1) the line "root (hd1,7)" is supposed to point to the partition with /boot on it, and (2) the "(hdx,y)" notation starts at zero, not one, so hdb1 is actually (hd1,0).

---

### Post by ubuntu-mike022465 on 2006-03-13
[QUOTE=Lux Perpetua]Oh, wait a sec. It looks like my previous post doesn't apply. I don't know what "root=Label=/" means, but I believe that (1) the line "root (hd1,7)" is supposed to point to the partition with /boot on it, and (2) the "(hdx,y)" notation starts at zero, not one, so hdb1 is actually (hd1,0).[/QUOTE]

I do understand that grub starts labelling drives and partitions at 0.

I've tried from grub, selecting my fedora entry, and doing typing "e" to edit my boot parameters.  I've tried various combinations of root (hd..., and ...) and got no joy.

In my set up, my ubuntu drive is a primary master (hd0,0), and with fedora as slave on the same IDE cable with (hd0,0)  designation in grub as well.  

But in gparted, ubuntu will show up as hda and fedora as hdb.

Still shaking my head on this... :-k 

M.  :-D

---

### Post by ubuntu-mike022465 on 2006-03-14
Bump.

---

### Post by ubuntu-mike022465 on 2006-03-15
Bumpity bump bump. :-D

---

### Post by ubuntu-mike022465 on 2006-03-15
Doing the hokey pokey now... :-P

---

