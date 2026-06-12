---
title: "Missing NTLDR, but I can see it sitting there..."
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by potatan on 2007-12-19
Hi,

When I select my windows disk using the BIOS, it boots up fine.  

However, when I point to it in GRUB's menu.lst, I get a missing NTLDR message after selecting Windows XP from the boot menu.

Windows is installed on the only (first) partition on /dev/sdc

fdisk -l output:

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74bfade6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10410    83618293+   7  HPFS/NTFS
/dev/sda2           10411       19536    73304595   83  Linux
/dev/sda3           19537       19929     3156772+   f  W95 Ext'd (LBA)
/dev/sda5           19537       19929     3156741   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb6256c92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c703c70

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9964    80035798+   7  HPFS/NTFS

---

### Post by Herman on 2007-12-19
What does the bottom portion of your /boot/grub/menu.lst look like?

---

### Post by potatan on 2007-12-19
Are you ready for this?  I've been, ahhh, experimenting.  :-) 

I have tried several different settings as you can see, the last one (Attempt 8 ) is the one that gives the NTLDR error.  All the others (and I know there are duplicates) give either Error 21 or Disk Read Error, as indicated in the comments against each attempt.

### 
#Attempt 1	Default entry as installed    *** Error 21
title		Microsoft Windows XP Professional 1
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

#Attempt 2	*** Disk read error - press CTRL-ALT-DEL
title		Microsoft Windows XP Professional 2
root		(hd0,0)
savedefault
makeactive
map		(hd2) (hd0)
map		(hd0) (hd2)
chainloader	+1

#Attempt 3	*** Error 21
title		Microsoft Windows XP Professional 3
root		(hd2,1)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

#Attempt 4     	Without MAP commands *** Error 21 
title		Microsoft Windows XP Professional 4
root		(hd2,0)
savedefault
makeactive
#map		(hd0) (hd2)
#map		(hd2) (hd0)
chainloader	+1

#Attempt 5 	Changed maps to include partition ***Error 21
title		Microsoft Windows XP Professional 5
root		(hd2,0)
savedefault
makeactive
map		(hd0,0) (hd2,0)
map		(hd2,0) (hd0,0)
chainloader	+1

#Attempt 6 	Tried removing maps *** Error 21
title		Microsoft Windows XP Professional 6
root		(hd2,0)
savedefault
makeactive
# map		(hd0,0) (hd2,0)
# map		(hd2,0) (hd0,0)
chainloader	+1

#Attempt 7 	Fdisk thinks Windows is on drive 1, partition 1 so trying as hd0,0 *** Disk read error
title		Microsoft Windows XP Professional 7
root		(hd0,0)
savedefault
makeactive
map		(hd2) (hd0)
map		(hd0) (hd2)
chainloader	+1

#Attempt 8 	Trying hd0,0 with no maps *** NTLDR Missing
title		Microsoft Windows XP Professional 8
root		(hd0,0)
savedefault
makeactive
#map		(hd2) (hd0)
#map		(hd0) (hd2)
chainloader	+1


Remember, Windows boots fine when I set it as the first disk in the BIOS, so I just need to get Grub to point to the correct place

Thanks in advance

---

### Post by forestpixie on 2007-12-19
you kept on going then :)

---

### Post by potatan on 2007-12-19
Never give up...!

---

### Post by logos34 on 2007-12-19
post your /boot/grub/device.map

Are you sure it's sdc1 and not sdb1 you want?  (the latter also appears to have a bootable [*] ntfs partition)

Try this to verify grub drive designation:

sudo grub

> geometry (hd2)

---

### Post by potatan on 2007-12-19
device.map:

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc


geometry:

grub> geometry (hd2)
drive 0x82: C/H/S = 9964/255/63, The number of sectors = 160086528, /dev/sdc
   Partition num: 0,  Filesystem type unknown, partition type 0x7

for completeness:
grub> geometry (hd1)
drive 0x81: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/sdb
   Partition num: 0,  Filesystem type unknown, partition type 0x7

grub> geometry (hd0)
drive 0x80: C/H/S = 19929/255/63, The number of sectors = 320173056, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82

---

### Post by logos34 on 2007-12-19
> #Attempt 1 Default entry as installed *** Error 21
title Microsoft Windows XP Professional 1
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

That should have worked.  Hmm...

---

### Post by potatan on 2007-12-19
That's kind of what I was thinking too.

/dev/sdb1 does have a bootable partition according to GParted, but I think this is left over from some previous ancient configuration of this PC (well before I started using Ubuntu).  Now it just contains data, no OS present on that drive.

---

### Post by Herman on 2007-12-19
>  When I select my windows disk using the BIOS, it boots up fine.  

However, when I point to it in GRUB's menu.lst, I get a missing NTLDR message after selecting Windows XP from the boot menu.

Windows is installed on the only (first) partition on /dev/sdc
My thinking is that Windows is in your third hard disk, first partition but when you boot it from the BIOS it becomes your first hard disk, first partition temporarily, so it boots okay.
Was it installed as the first hard disk, first partition?
In other words, is your boot.ini file in Windows set up to boot Windows in a first hard disk, first partition?
Then you added the extra hard disks?
In any case, Linux, (and probably GRUB) seem to want to boot it as a third hard disk, first partition.

You might want to try editing your boot.ini file accordingly, if you want to boot it with GRUB. That's my guess.
"[ NTLDR is missing, press any key to restart]("http://users.bigpond.net.au/hermanzone/p15.htm#NTLDR_is_missing_press_any_key_to")." is a Windows booting error, so this is happening after GRUB has already done everything right, so you need to look in Windows for the problem.

Regards, Herman :)

---

### Post by potatan on 2007-12-19
I like your thinking.  I'll go and have a look into boot.ini and return with any news!

---

### Post by Herman on 2007-12-19
If your boot.ini file looks like this:
```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk([COLOR=Red]**0**[/COLOR])partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk([COLOR=Red]**0**[/COLOR])partition(1)WINDOWS="Microsoft Windows Xp Home Edition" /fastdetect
```You might want to try changing it to this:
```
[boot loader]
timeout=30
default=multi(0)disk([COLOR=Sienna]**2**[/COLOR])rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk([COLOR=Sienna]**2**[/COLOR])partition(1)WINDOWS="Microsoft Windows Xp Home Edition" /fastdetect
``` (I think that would be right, but I'm not as well practiced with boot.ini as with GRUB, so I hope I'm right).

Here is a link that shows how to gain access to the file for editing, as it is a 'hidden', 'System', 'Read-only' file unless you know what to do to open it. 
Just read the first part of this link, the rest is about something else, [http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)
That's the way I do it anyway, if you know an easier way then feel free to do it your way.

Regards, Herman :)

---

### Post by potatan on 2007-12-19
Thanks - I got there (kind of), before your post.

All I did was change the first [operating systems] entry to disk(2), and it booted (after offering me a choice of Windows or, umm, Windows)

I'll try changing the default rdisk entry too to see if this final issue can be fixed - but I'm in Windows territory now so I'll end this thread

Thanks everyone for your help in tracking this down.

Of course, it'll all go wrong again I expect when I reconnect my internal IDE drive, but I feel that I'm in a much better position to troubleshoot any further problems now.  

Cheers!

---

### Post by Herman on 2007-12-19
Okay, good luck with it and keep us posted on how you get along, I would still be interested in what you need to do and it might help us to help others.

Regards, Herman :)

---

### Post by potatan on 2007-12-19
Well I haven't managed to completely sort out the spurious boot.ini entry displaying at Windows startup:

see windows-boot-options.jpg 

this is my current boot.ini:
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(2)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


and diskmanagement.png gives a picture of what Windows thinks my disks are.

Finally, bios-disk-order.jpg shows the disk order in BIOS

Hopefully all this may help with others' problems

for info, it's an ASUS A8V Deluxe motherboard with one disk on the VIA controller (80GB Windows) and 2 disks on the Promise controller (160GB and 250GB)

Right - I've been playing with this most of today so it's time for a pint I reckon!

---

### Post by Herman on 2007-12-19
Yes, well it's a strange one. 
Normally it isn't necessary to need to edit boot.ini when setting up a dual boot between Ubuntu and Windows. The pair of 'map' commands should handle it.

I can't see anything wrong with your original entries though, 
```
 title        Microsoft Windows XP Professional 1
root        (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

``` ```
Device Boot Start End Blocks Id System
/dev/sdc1 * 1 9964 80035798+ 7 HPFS/NTFS
``` That should boot it okay, (as logos34 said already), but then you are getting the NTLDR is Missing Error, which I have always associated with an out of date of erroneously edited boot.ini file.

So you did get it working then eh? Did editing boot.ini fix the problem?

About the spurious Windows entry, could that be for a Windows Recovery partition of some kind?

I am wondering if it might have something to do with the controller cards too?

Thanks for your feedback, some of us do take notice and keep track of things like this in case another similar question comes up again.

Regards, Herman :)

---

### Post by logos34 on 2007-12-19
Might the spurious boot.ini entry in the first picture ('default') be showing up because windows thinks there are two OS listings when it's actually one and the same:

[boot loader]
timeout=3
**default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S**
[operating systems]
**multi(0)disk([COLOR="Red"]2[/COLOR])rdisk(0)partition(1)\WINDOWS**="Micro soft Windows XP Professional" /noexecute=optin /fastdetect 

i.e. the discrepancy on 'disk' ?? 

But frankly that's what is confusing me: I thought this is the line we want

...multi(0)disk(0)rdisk(0)partition(1)...

From this windows think its the first disk, and when we chainlaod NTLDR in third position we use the 'map' lines to continue to fool it into thinking it's the first boot drive?

---

