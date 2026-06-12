---
title: "Adding XP after Ubuntu: Drive Labeling Order?"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by Explodicide on 2008-05-12
I've got WinXP on an SATA drive, another SATA drive for storage, an IDE drive for storage, and another 80GB IDE drive that I just slapped in for Ubuntu.  

I had some weird issues installing Ubuntu 8.04 to the 80GB IDE drive; Grub freaked out and refused to boot either Windows or Linux.  So I unplugged all of the drives except the 80GB IDE drive, and installed Ubuntu.  So far so good, it runs fine.  

Now, I'm not quite sure how to add Windows to the Grub config file.  Here's why: When I set the system up, Ubuntu set up the IDE drive as sda, and mapped that to hd0.  Now, when I do an fdisk -lu, it's telling me that the 500GB drive that I set up for Windows is sda, and the IDE drive that Ubuntu is on is sdd.

I've tried adding sdb through sdd to the device.map file, and specifying them like this:
```
title		Windows XP
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0) 
chainloader +1
```
but that just fails every time, saying that the bootloader is missing, press Ctrl+Alt+Del to restart (that's a Windows error, so I presume it's hitting one of my storage drives and failing to find a boot.ini).  I've also tried specifying the drive handle in the Grub boot, like:
```
root (sda,0)
```
but I'm pretty sure I've got the syntax wrong there.  

Not quite sure how to proceed here, and I figured I'd ask, as I've already had to reinstall 'cause I mucked something up and Grub stopped being able to find Ubuntu.  

This is my device.map file:
```

(hd0)	/dev/sda
```

This is the output of fdisk -lu (shortened for readability):
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes  //Windows
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfb58fb58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976751999   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes //SATA Storage

Disk /dev/sdc: 122.9 GB, 122942324736 bytes //IDE Storage

Disk /dev/sdd: 80.0 GB, 80026361856 bytes //the 80GB IDE drive
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2d402d3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   150239879    75119908+  83  Linux
/dev/sdd2       150239880   156296384     3028252+   5  Extended
/dev/sdd5       150239943   156296384     3028221   82  Linux swap / Solaris
```

And this is what I have for booting Ubuntu in menu.lst:
```

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e98f4358-a7cb-497e-8b81-25eb5bd05b27 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
```

Thanks in advance, and sorry for what's kindof a repost.  I know that Grub configuration is a common issue, but so far I haven't seen anyone with a similar issue to mine.

---

### Post by confused57 on 2008-05-12
You can try several Windows entries in grub, one of them should work:
```
title		Windows XP on hd1
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0) 
chainloader +1
```

```
title		Windows XP on hd2
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0) 
chainloader +1
```

and you can even try a Windows entry as hd3...add them to the very bottom of your menu.lst(after the line ###END DEBIAN AUTOMAGIC KERNELS LIST.  Just keep the one that works & delete the others.

---

### Post by Explodicide on 2008-05-12
I tried that.  None of them, from hd1 to hd3, worked.

---

### Post by confused57 on 2008-05-12
> **Explodicide said:**
> I tried that.  None of them, from hd1 to hd3, worked.
I thought one of them might work...did you change the map lines accordingly? e.g.
root (hd0,2)
map (hd0) (hd2)
map (hd2) (hd0)

---

### Post by Explodicide on 2008-05-12
> **confused57 said:**
> I thought one of them might work...did you change the map lines accordingly? e.g.
root (hd0,2)
map (hd0) (hd2)
map (hd2) (hd0)

Yup, tried that. Is there a way to get grub to tell me what it's seeing for useable drives from the console?  It'd be nice to have some more info about what's going on.

---

### Post by confused57 on 2008-05-13
> **Explodicide said:**
> Yup, tried that. Is there a way to get grub to tell me what it's seeing for useable drives from the console?  It'd be nice to have some more info about what's going on.
You mentioned in your first post you were adding the entry to your device.map, if this is what you actually did, you need to add the entries to your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

When you boot first to your Ubuntu drive, you should see your Windows entry along with your Ubuntu boot entries.

---

### Post by Explodicide on 2008-05-13
Yeaaah.  Gotta apologize for wasting people's time.  I went back and checked my menu.lst entry, and found a typo.  
```

map (hd0) (hd3)
map (hd2) (hd0)
```

I guess when I was testing the hd3 entry I missed changing one of the lines.  
It still doesn't make much sense to me, but it's working.  

:oops:

Actually, it worked ONCE going to (hd3), but then I rebooted and it tried to go to some weird Dell diagnostic thing (the OEM XP disk I used had some Dell stuff on it, but my computer's not a Dell...) and I had to switch it to (hd2) to get it to boot.  Weird. . . 

Thanks for all who tried to help me.

---

