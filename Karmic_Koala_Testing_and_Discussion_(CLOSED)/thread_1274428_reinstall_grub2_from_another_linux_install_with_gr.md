---
title: "reinstall grub2 from another linux install with grub2"
date: 2009-09-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by iDIEDaLONGtimeAGO on 2009-09-24
Hi, i just installed karmic to give it a try. I installed grub2 on the root partition. My mbr has grub2-gfxmenu from arch. My problem's that ubuntu wouldnt boot. I tried chainloading but it doesnt work. I copied the relevant lines from ubuntu's grub.cfg into arch's grub.cfg but it still didnt work. I thought i'd try reinstalling grub again but here's my problem. My cdrom's suddenly screwed so i cant use a live cd. Now i can i boot into my other linux installs and issue grub-install /dev/sda7(ubuntu's on sda7 without a separate /boot) without messing up the other grubs??
thanks for any advice.

---

### Post by philinux on 2009-09-24
Thats where I put grub2 from the live cd. Disk 2 partition 1.
I use this to boot grub2 karmic from the legacy grub.

```
title        SDB Karmic

root (hd1,0)
chainloader +1
```

That way it dont mess with my grub on my mbr disk 1.

---

### Post by iDIEDaLONGtimeAGO on 2009-09-24
> **philinux said:**
> Thats where I put grub2 from the live cd. Disk 2 partition 1.
I use this to boot grub2 karmic from the legacy grub.

```
title        SDB Karmic

root (hd1,0)
chainloader +1
```

That way it dont mess with my grub on my mbr disk 1.

hmm, i already tried chainloading. My mbr grub is also a grub2. so my ubuntu entry is 
```
menuentry "Ubuntu (sda7)" {
set root (hd0,7)
chainloader +1
}
```
but it doesnt work. Thanks for the reply, nevertheless

---

### Post by philinux on 2009-09-24
If grub 2 is installed on your sda7 then will running update-grub from the mbr grub2 not pick it up?

---

### Post by iDIEDaLONGtimeAGO on 2009-09-24
i tried it, it adds a section for ubuntu (which is exactly the same as in ubuntu's grub.cfg'
here it is.
```
menuentry "Ubuntu, Linux 2.6.31-10-generic" {
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 8be61f05-2052-4301-a89b-2207b6a6005a
	linux	/boot/vmlinuz-2.6.31-10-generic root=UUID=8be61f05-2052-4301-a89b-2207b6a6005a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-10-generic
```

but it doesnt work...displays an error
```
incorrect command "initrd"
```
and i chainload , the next screen says 
```
Press any key to continue
``` and freezes there.
Any more ideas?

---

### Post by philinux on 2009-09-24
> **iDIEDaLONGtimeAGO said:**
> i tried it, it adds a section for ubuntu (which is exactly the same as in ubuntu's grub.cfg'
here it is.
```
menuentry "Ubuntu, Linux 2.6.31-10-generic" {
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 8be61f05-2052-4301-a89b-2207b6a6005a
	linux	/boot/vmlinuz-2.6.31-10-generic root=UUID=8be61f05-2052-4301-a89b-2207b6a6005a ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-10-generic
```

but it doesnt work...displays an error
```
incorrect command "initrd"
```
and i chainload , the next screen says 
```
Press any key to continue
``` and freezes there.
Any more ideas?

I assume the missing } is just a copy and paste thing?

---

### Post by iDIEDaLONGtimeAGO on 2009-09-24
exactly, its just a copy paste thing. The lines are fine in grub's config.
Maybe i'll just try a reinstall. Thanks for ur help

---

### Post by VMC on 2009-09-24
> **iDIEDaLONGtimeAGO said:**
> Hi, i just installed karmic to give it a try. I installed grub2 on the root partition. My mbr has grub2-gfxmenu from arch. My problem's that ubuntu wouldnt boot. I tried chainloading but it doesnt work. I copied the relevant lines from ubuntu's grub.cfg into arch's grub.cfg but it still didnt work. I thought i'd try reinstalling grub again but here's my problem. My cdrom's suddenly screwed so i cant use a live cd. Now i can i boot into my other linux installs and issue grub-install /dev/sda7(ubuntu's on sda7 without a separate /boot) without messing up the other grubs??
thanks for any advice.Did you install karmic boot to its partition? Chainload needs that info.

---

