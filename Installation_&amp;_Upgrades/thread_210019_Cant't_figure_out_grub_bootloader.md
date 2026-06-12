---
title: "Cant't figure out grub bootloader"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by tcollogne on 2006-07-06
Hi all,

I have just installed ubuntu on my pc. The pc has 2 hard disk, 1 ide with linux (hda) and 1 sata with windows xp (sda).

I use my hda (linux) disk as primary boot disk, so I want to add the windows entry to my grub bootloader.

The first problem is : I don't see the boot menu. How can I enable the menu?

The second problem : What do I need to add to menu.lst file in orde to start windows?

I have found somewhere that I need to add this

title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Ok, but I have no idea what I need to put next to root. Now it states (hd0,0).
Do I need to put (sd0,0)? How can I figure this out?

Thanks.

---

### Post by simonn on 2006-07-06
[QUOTE=tcollogne]
The first problem is : I don't see the boot menu. How can I enable the menu?
[/quote]


What do you see? What does it boot into?

> 
Ok, but I have no idea what I need to put next to root. Now it states (hd0,0).
Do I need to put (sd0,0)? How can I figure this out?


It depends on your bios settings.

Your first boot hard drive should be (hd0), your second (hd1). It does not matter if it is SATA or IDE.

---

### Post by dickohead on 2006-07-06
I too am using both an ATA/IDE hdd and a SATA drive, but when I tried to boot windows from my Grub boot loader - nothing.
The only way I found to boot into both hard drives was to use my motherboards boot device feature (F12) and select either HDD1 or HDD2 to boot from when booting up. I'm sure you can set Grub up to boot to the windows drive, but i've not bothered looking.

So to set your Grub HDD as primary, you will need to alter your BIOS settings to boot from that drive first, then try and configure Grub to load windows.

Good luck!

---

### Post by simonn on 2006-07-06
What you need to do is to install grub on the MBR of the first boot device and tell it where /boot/grub is.

This can be tricky when you have mixed drive types, e.g. PATA and SATA, in the same PC as it depends on the bios (and what the user sets in the bios) as to where it looks to boot.

The first step in this scenario is to force grub to map the drives a specific way.

To do this, create the file /boot/grub/device.map with a text editor, e.g. 

```

$ sudo nano /boot/grub/device.map

```


With the following contents:

```

(hd0)	/dev/hda
(hd1)	/dev/sda

```

This will force the grub shell to map /dev/hda to (hd0) and /dev/sda to (hd1) 

Next, we need to tell grub where to look for /boot/grub and to install itself to the MBR.

Start the grub shell:

```

$ sudo grub

```

In the grub shell, we tell grub what partition to look for /boot/grub on.

```

> root (hd0,0)

```

In this case it would be hda1.
Grub device numberind are sort of like:

hd0 = hda
hda0,0 = hda1
hda0,1 = hda2
...
hda1 = hdb
hda1,0 = hdb1
hda1,1 = hdb2
...

Of course as we have a SATA drive and have mapped it to (hd1) our machine would be more like 

hd0 = hda
hda0,0 = hda1
hda0,1 = hda2
...
hda1 = sda
hda1,0 = sda1
hda1,1 = sda2
....

If /boot/grub was on sda1, we would use root (hd1,0).

Next, we want to write grub to the MBR, still in the grub shell:

```

> setup (hd0)

```

If we wanted to write to the MBR on sda0, we would use setup (hd1).

Now we quit the grub shell

```

> quit

```

If you now reboot, assuming the drive order in the bios is correct, the grub menu should come up and you should be able to boot into linux ok.

You are correct in needing something like the below to boot into windows.

```

title Microsoft Windows
root (hd0,0)
savedefault
makeactive
chainloader +1

```

The root depends on what partition you have installed windows to. Assuming it is on sda1 and sda is the second disk in your bios boot order, is should be root (hd1,0) i.e. disk 1 (second disk), partition 0.

---

### Post by tcollogne on 2006-07-06
I have tried what was written, but it doesn't work.

This my the result of fdisk

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433        9039    53070727+   f  W95 Ext'd (LBA)
/dev/sda5            2433        9039    53070696    7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2852    22908658+  83  Linux
/dev/hdb2            2853        9729    55239502+   f  W95 Ext'd (LBA)
/dev/hdb5            2978        7440    35849016    7  HPFS/NTFS
/dev/hdb6            7441        9729    18386361    7  HPFS/NTFS
/dev/hdb7            2853        2977     1003999+  82  Linux swap / Solaris


So I added the following to menu.lst

title Microsoft Windows
root (hd0,0)
savedefault
makeactive
chainloader +1

When I select that entry, I get the text on the screen saying that the partition has an unknown filesystem, and then nothing happens.

Any other ideas?

---

### Post by simonn on 2006-07-06
If you are getting a grub menu, then it is unlikely that your SATA disk is hd0. It is probably hd1.

So, change:

```

root (hd0,0)

```

to:

```

root (hd1,0)

```

---

### Post by tcollogne on 2006-07-07
Sorry, my mistake.

I allready put (hd1,0). I made a mistake in the post.

Any other ideas?

---

### Post by simonn on 2006-07-07
Try changing the chainloader line to 

```

chainloader (hd1,0)+1

```

Try hd0 in the above if it fails.

---

### Post by tcollogne on 2006-07-07
I have tried both. When I use hd0 I get the message

"invalid executable format"

---

### Post by tcollogne on 2006-07-09
I 've got it. I needed to add this to menu.lst

title		Windows XP Media Center Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

