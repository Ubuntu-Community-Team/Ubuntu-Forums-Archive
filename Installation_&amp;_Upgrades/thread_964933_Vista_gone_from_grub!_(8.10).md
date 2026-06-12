---
title: "Vista gone from grub! (8.10)"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by tegguN on 2008-10-31
Hey guys, I triple booted xp, vista and ubuntu up till yesterday when I decided to remove xp and reinstall ubuntu with 8.10. I repartitioned using the Ubuntu installer, removing the first 2 partitions and installing ubuntu onto there. However vista is now gone from grub, I've tried adding it with this in /boot/grub/menu.lst:

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1fdf447f-d068-44cd-ab53-5a9aea1322ee
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1fdf447f-d068-44cd-ab53-5a9aea1322ee ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Windows Vista
root		(hd0,0)
makeactive
chainloader	+1

and this:

title 		Vista
map 		(hd0) (hd1)
map 		(hd1) (hd0)
rootnoverify 	(hd1, 0)
makeactive
chainloader 	+1

but I always get an odd error, like non-executable file or something different each time I've tried to adjust the hd(0,x) settings.

here's my sudo fdisk -l

Disk /dev/sda: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29814   239480923+  83  Linux
/dev/sda2           29815       30505     5550457+   5  Extended
/dev/sda4           30506       43778   106607616    7  HPFS/NTFS
/dev/sda5           29815       30505     5550426   82  Linux swap / Solaris

Vista is on sda4, sda2 and sda5 look identical,and I don't know where sda3 is?

Can anyone help??

---

### Post by tegguN on 2008-10-31
no one? :(

---

### Post by caljohnsmith on 2008-10-31
First, since Vista is on sda4, try this in your menu.lst:
```
title Windows Vista
root [COLOR="Blue"](hd0,3)[/COLOR]
makeactive
chainloader +1
```
That should work to boot Vista, but if you originally installed Vista after installing XP, you may be in for an unpleasant surprise; most likely Vista would have put all its boot files in the XP partition, so when you deleted the XP partition, you may have deleted Vista's boot files. But try the above Windows entry in your menu.lst first, and let me know exactly what happens when you try and boot Vista with it; we can work from there. :)

---

### Post by tegguN on 2008-10-31
okay so I tried that and got:

Bootmgr is missing
Ctrl + Alt + Del to restart

I think you might be right about the XP thing? :(

---

### Post by caljohnsmith on 2008-10-31
Unfortunately, yes, that error means your Vista boot files were deleted like I suspected. But the good news is that it shouldn't be hard to fix; if you have your Vista Install CD, just boot it up and do a "Vista Repair". Or if you don't have your Vista Install CD, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/") and do the same "Vista Repair." Let me know how it goes.

---

### Post by tegguN on 2008-10-31
I tried recovering it with my vista cd and it discovered the partition and said it was recovering, still the same Bootmgr message though? :S

---

### Post by tegguN on 2008-10-31
although there is a boot folder in the root of the windows partition which I'm not sure was there before

---

### Post by blazemore on 2008-10-31
Boot from the Vista DVD
Don't let it do an "Automatic" startup recovery thing
Open a recovery console or whatever it calls it
Do:
bootrec /fixboot

That has solved similar problems for me.
Bootmgr is the Windows bootloader

---

### Post by tegguN on 2008-10-31
It works!

The first time I ran the recovery disc something odd happened. I downloaded the one off the site earlier, burnt it and ran it and did an automatic repair and

```
bootrec /fixboot
```

and everything works!

---

