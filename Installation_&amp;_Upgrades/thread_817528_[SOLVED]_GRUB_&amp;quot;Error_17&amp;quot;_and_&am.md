---
title: "[SOLVED] GRUB &amp;quot;Error 17&amp;quot; and &amp;quot;Error 12&amp;quot; after 8.04 installation"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by tark on 2008-06-03
Here's my problem:

I had two functional operative systems on my pc (Windows XP and Ubuntu 7.10) until i decided to install the new Ubuntu 8.04 with the official cd i received via mail.

During the installation of the 8.04, i formatted the previous (and only one) ext3 partition on my secondary hard disk. but after the final reboot GRUB failed to load both windows and linux:

- if i try to load Windows XP i get "ERROR 12: invalid device request"
- if i try to load Ubuntu 8.04 i get "ERROR 17: cannot mount selected partition"

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a101f5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1249       19929   150055132+   f  W95 Ext'd (LBA)
/dev/sda2   *           1        1248    10024528+  83  Linux
/dev/sda5            1307       19929   149589216    7  HPFS/NTFS
/dev/sda6            1249        1306      465822   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85648564

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sdb2            1276        7476    49809532+   5  Extended
/dev/sdb5            1276        7476    49809501    7  HPFS/NTFS

```

Could somebody help me with this? I would like to get back both windows and linux working again.

---

### Post by logos34 on 2008-06-03
Select hardy 8.04 on the grub menu, press 'e' to edit, 'e' again on the 'root' line and change from (hd1,1) to (hd0,1), or vice-versa.  'b' to boot.  If it gets you into ubuntu, make the change permanent:

gksudo gedit /boot/grub/menu.lst

change the 'groot' and 'root' lines accordingly. Windows will be be either (hd0,0) or (hd1,0).  

If the latter, you need [map lines like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

---

### Post by tark on 2008-06-03
> **logos34 said:**
> Select hardy 8.04 on the grub menu, press 'e' to edit, 'e' again on the 'root' line and change from (hd1,1) to (hd0,1), or vice-versa.  'b' to boot.could i do this directly modifying */boot/grub/menu.lst* with a text editor?

---

### Post by Living2007 on 2008-06-03
> **tark said:**
> could i do this directly modifying */boot/grub/menu.lst* with a text editor?
This may help both problems and describe what would have gone wrong.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Use the "find" function in your browser and type "Error 12" and "Error 17"

---

### Post by meierfra. on 2008-06-03
> could i do this directly modifying /boot/grub/menu.lst with a text editor?

Yes you can. But you would have to mount your ubuntu partition first. Also if you do it "logos34" way, you will immediately see whether it worked or not. If it didn't, you can try different numbers.  So "logos34" way usually works out better.

---

### Post by tark on 2008-06-04
> **logos34 said:**
> Select hardy 8.04 on the grub menu, press 'e' to edit, 'e' again on the 'root' line and change from (hd1,1) to (hd0,1), or vice-versa.  'b' to boot.  If it gets you into ubuntu, make the change permanent:

gksudo gedit /boot/grub/menu.lst

change the 'groot' and 'root' lines accordingly. Windows will be be either (hd0,0) or (hd1,0).  

If the latter, you need [map lines like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").
I entered the grub menu at startup and, as you said, modified *root* line from *(hd0,1)* to *(hd1,1)* and now my 8.04 boots correctly. I did the same modifies to * menu.lst* so changes are permanent now.

however, in my *menu.lst* there isn't any *groot* line to modify. there are a few but as examples...

i did the same modify to *root* line for windows, i changed it from *(hd1,0)* to *(hd0,0)* but still windows don't want to boot.

```

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=431314d8-5649-4313-8c86-10453548c828 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=431314d8-5649-4313-8c86-10453548c828 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
#makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

any suggestions?

ps. thanks a lot for your help, everybody!

---

### Post by confused57 on 2008-06-04
You'll need to remove the map lines for root (hd0,0):
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

There should be a groot line near the top of your menu.lst, here's the relevant section of mine:
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```

---

### Post by tark on 2008-06-04
> **confused57 said:**
> You'll need to remove the map lines for root (hd0,0):
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

I already tried to remove maps but it doesn't work. I don't get error code 12 anymore, grub seems to work now but windows still won't load.

> There should be a groot line near the top of your menu.lst, here's the relevant section of mine:
```

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

```You mean this part? I have it but as yours it is commented. What i have to do?

---

### Post by tark on 2008-06-04
Another question...

The hard disk where i putted Windows XP is a 60GB **ATA** (sdb with *fdisk -l*). Isn't it weird? I mean, shouldn't it be named **h**db?

---

### Post by logos34 on 2008-06-04
> **tark said:**
> Another question...

The hard disk where i putted Windows XP is a 60GB **ATA** (sdb with *fdisk -l*). Isn't it weird? I mean, shouldn't it be named **h**db?

yeah, it confuses a lot of people...the reason is ubuntu has switched (several releases ago, actually) to the libata storage driver/module, which sees everything as if it were a scsi device.  In practice, though, the implentation seems uneven and varies according to hardware/your specific storage controller--for instance, my ide drives (nvidia chipset) are still seen by 8.04 hardy as 'hd?' in all but the latest kernel updates (-17, -18 which now  designate them as 'sd?').

The 'groot' line should have the hash ('#') mark. Again, confusing because grub ignores such lines below the 'Automagic' section

So yours should read:

> # groot=(hd1,1)

Sorry I was not clearer in my initial response i.e. the 'map' lines--I should have also explicit said to **remove** them if grub was on the windows drive. 

But that doesn't explain why windows refuses to boot.

I was just assuming that your bootable windows partition (C: drive) was sdb1, the one marked '*'.  Maybe it's sdb5? (unlikely since it's a logical partition).  What is on that ntfs partition sda5? data storage?

---

### Post by tark on 2008-06-04
> **logos34 said:**
> The 'groot' line should have the hash ('#') mark. Again, confusing because grub ignores such lines below the 'Automagic' sectionSo if i modify groot string into *# groot=(hd1,1)* i should run update-grub after, right? And how can i see in which drive grub is installed? I'm not sure it is in sdb...
Since i installed ubuntu after windows, i always thought the drive with windows is the primary. but why fdisk shows it as sd**b** and not sd**a**?

i'll try to modify groot as soon as i back home.

> I was just assuming that your bootable windows partition (C: drive) was sdb1, the one marked '*'.  Maybe it's sdb5? (unlikely since it's a logical partition).  What is on that ntfs partition sda5? data storage?sdb5 and sda5 are just data. Windows XP is installed in sdb1 (the 10GB partition).

---

### Post by logos34 on 2008-06-04
> **tark said:**
> So if i modify groot string into *# groot=(hd1,1)* i should run update-grub after, right? And how can i see in which drive grub is installed? I'm not sure it is in sdb...

Get the updates first (-18 kernel et al).  Then run sudo update-grub.  (Hope that update doesn't break anything--I had to go to back to using -16 because suspend and hibernate won't work.)

Grub (stage1) is definitely on the MBR of sdb (bios boot disk), pointing to menu.lst on the linux root hd1,1 (second drive, second partition).  

> Since i installed ubuntu after windows, i always thought the drive with windows is the primary. but why fdisk shows it as sd**b** and not as**a**?

fdisk does not arrange them in bios boot order. In the case of ide drives, sda (actually 'hda') corresponds to primary master, sdb/hdb = primary slave, sdc/hdc=secondary master, sdd/hdd=secondary slave

---

### Post by meierfra. on 2008-06-04
> but windows still won't load.

Any error messages?

Did you delete any partitions when you installed Ubuntu?

---

### Post by tark on 2008-06-04
> **meierfra. said:**
> Any error messages?
No, if i try to boot windows nothing happens just the grub "Starting up..." message.

> Did you delete any partitions when you installed Ubuntu?While installing 8.04, i only formatted the previous ext3 partion. In fact, if i run the 8.04, all partions in the 2 drives i have mounts correctly (even the windows xp partition).

---

### Post by logos34 on 2008-06-04
grub appears to be chainloading windows correctly, but there is some problem on the xp side.  The fact that you can mount windows partitions ok in linux makes it unlikely that filesystem errors are at issue here (although I could be wrong)

maybe running 
[B]
fixboot c:[/B]

from XP install CD recovery console would help.

?

---

### Post by tark on 2008-06-04
> **logos34 said:**
> maybe running 
[B]
fixboot c:[/B]

from XP install CD recovery console would help.

?**It worked!!**
that was the missing brick! thank you logos and thanks to everyone helped me! ^^

---

### Post by logos34 on 2008-06-04
ok, glad to hear everything works now

enjoy

---

### Post by theumang on 2008-06-05
Hey Tark

why don't you mark this thread as solved ?

its under the thread tools.

Thanks
Umang

---

