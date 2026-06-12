---
title: "USB Problems"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by peddy on 2007-10-20
Hey everyone
I upgraded to Ubuntu Gutsy 64 bit on Friday, and I have been having a problem with any USB flash sticks, or mass storage devices for that matter. Whenever I insert any media of that sort, this message pops up:

```
Cannot mount volume:
Unable to mount volume
details>> 
mount: wrong fs type, bad option, bad superblock on /dev/sdc,    missing codepage or helper program, or other error      In some cases useful info is found in the syslog- try dmesg | tail or so 

```

and 'dmesg | tail'  gives me
```
 [  126.451554] 
SCSI device sdc: 8026112 512-byte hdwr sectors (4109 MB)
[  126.452176] sdc: Write Protect is off
[  126.452178] sdc: Mode Sense: 03 00 00 00
[  126.452180] sdc: assuming drive cache: write through
[  126.453924] SCSI device sdc: 8026112 512-byte hdwr sectors (4109 MB)
[  126.454547] sdc: Write Protect is off
[  126.454549] sdc: Mode Sense: 03 00 00 00
[  126.454551] sdc: assuming drive cache: write through
[  126.454555]  sdc: sdc1
[  126.670605] FAT: Unrecognized mount option "usefree" or missing value

```
I have tried several ports and media devices. Anybody have any idea whats going on?

Thanks
Peddy

---

### Post by peddy on 2007-10-20
OK, tested USB in Feisty LiveCD, and it is working fine. Maybe hardware incompatibility? My mobo is Asus P5B-E.

Thanks for any help

---

### Post by peddy on 2007-10-21
*hate* to do this, but *bump*

---

### Post by Eric the Red on 2007-10-21
try 'fdisk -l' to see if you're mounting the right drive
then use the *'mount /dev/sdb1 /mnt/usb1'* command manually.

---

### Post by peddy on 2007-10-21
Its visible in Computer, but when I click on the icon, same message as before.

Any ideas?

---

### Post by Eric the Red on 2007-10-21
post your 'cat /etc/fstab' log here .. if you don't have one, you might be able to solve the issue by creating your own '/etc/fstab' entry.

---

### Post by peddy on 2007-10-21
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=1e174738-d232-4ab9-b26e-0c76abe8bc16 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb9
UUID=57ccc6ea-63b7-4007-afec-0e87b35f1806 /home           ext3    defaults        0       2
# /dev/sdb8
UUID=ede34a3d-04f8-452d-ab71-f05f907f13d6 /tmp            ext3    defaults        0       2
# /dev/sdb5
UUID=27983134-8517-4485-831e-9442e7225ece /usr            ext3    defaults        0       2
# /dev/sdb6
UUID=b23a01c2-6839-4e9c-9e61-538fd01b3ae2 /var            ext3    defaults        0       2
# /dev/sdb7
UUID=545e1804-24a3-4433-ac18-75c7eb790e90 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


```

Thanks

---

### Post by peddy on 2007-10-21
Bump (sorry!)

---

### Post by peddy on 2007-10-22
I have verified that the problem is with fat or fat32 partitions.

---

### Post by photohikaru on 2007-10-26
i had the same problem as you, with a fat32 partition on an external hard drive.  i still don't know exactly what the cause was, but try a very simple fix that worked for me:

go to places>computer and right click on the drive that isn't mounting properly.  select properties, and go to the 'volume' tab.  under 'settings' set the name of the volume to whatever you have it named as (this may not be necessary, but i did it and it worked; for me it was 'FAT32').  then (and this is probably the important step) in the 'mount options' field, type a space (this, apparently, clears any other options which aren't visible in the properties window).  then close the properties window.  the drive mounted on my next boot, and every time after that.

---

### Post by cheesey_toastie on 2007-10-27
Excellent photohikaru!   This same problem had been annoying me for about 2 hours!  I've seen no end of topics with people with problems similar to this - I bet this fix will work for the others!

---

### Post by photohikaru on 2007-10-28
wow.  my first time helping someone with an ubuntu problem.  i'm happy.  now i know why so many other people are doing it. :)
 i still wonder what the cause was.  i mean, i assume it's the 'usefree' option that the drives are mounting with, but where is that information stored?

---

### Post by peddy on 2007-10-28
The fix is the last post; works for me
[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025)

I actually found this fix before photohikaru posted, I just didn't write the fix here (forgot)

---

### Post by photohikaru on 2007-10-28
i see.  thanks!

---

### Post by ossi on 2007-10-29
Ok, and how do you solve this, if you are using KDE?

---

### Post by ossi on 2007-10-31
Was a Kernel Problem. Solved here: [http://ubuntuforums.org/showthread.php?t=594829]("http://ubuntuforums.org/showthread.php?t=594829")

---

### Post by Dusenberg on 2007-10-31
> **photohikaru said:**
> i had the same problem as you, with a fat32 partition on an external hard drive.  i still don't know exactly what the cause was, but try a very simple fix that worked for me:

go to places>computer and right click on the drive that isn't mounting properly.  select properties, and go to the 'volume' tab.  under 'settings' set the name of the volume to whatever you have it named as (this may not be necessary, but i did it and it worked; for me it was 'FAT32').  then (and this is probably the important step) in the 'mount options' field, type a space (this, apparently, clears any other options which aren't visible in the properties window).  then close the properties window.  the drive mounted on my next boot, and every time after that.

Hi, sorry to jump in, but I need some help with similar problem.

I've just installed 7.10 on my laptop and am having problems copying files from my usb hard drive (fat32). When I try and copy a 1Mb file from the drive to my laptop I get a 'copying....' pop-up and a progress bar that is estimated at 30+ mins. Then after a few seconds I get an I/O error popup and that's that.  Now the odd thing is I can copy a small file (59kb) without probs.  If I try and open a  movie on the external drive from RealPlayer nothing seems to happen for a second or so then the player crashes and dies without comment.

USB sticks work fine and I can copy very large files in both directions. The 1mb file copies almost instantly.  The usb drive also perfectly works through my PC with both Fedora7 and XP.

I tried photohikaru's fix and it didn't work for me.  

Anyone any ideas please? :)

---

### Post by peddy on 2007-11-06
Try creating your own thread

---

### Post by numbah_one's on 2007-12-03
> **photohikaru said:**
> i had the same problem as you, with a fat32 partition on an external hard drive.  i still don't know exactly what the cause was, but try a very simple fix that worked for me:

go to places>computer and right click on the drive that isn't mounting properly.  select properties, and go to the 'volume' tab.  under 'settings' set the name of the volume to whatever you have it named as (this may not be necessary, but i did it and it worked; for me it was 'FAT32').  then (and this is probably the important step) in the 'mount options' field, type a space (this, apparently, clears any other options which aren't visible in the properties window).  then close the properties window.  the drive mounted on my next boot, and every time after that.

thank you so much! had the same problem and not its fixed..

---

### Post by shanerdaner on 2007-12-09
Thanks this fixed my F500 problem I appreciate it!

---

### Post by kutta on 2008-03-22
Thanks a lot and you saved me.Editing Mount options by right clicking on the drive worked.

---

