---
title: "Format a windows partition without killing grub"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by izzmit on 2008-09-20
Hi
Ok, so I installed Windows on a partition, and then installed ubuntu on the second partition.

I spent hours getting everything to work right on my Ubuntu (hardy)
and dont want to lose it.

I need to format my windows partition, but I dont wont to mess up my grub boot loader.

Will formatting windows partition (the main partition) overwrite the grub thing, or will my ubuntu remain untouched and bootable?

---

### Post by caljohnsmith on 2008-09-20
> **izzmit said:**
> 
Will formatting windows partition (the main partition) overwrite the grub thing, or will my ubuntu remain untouched and bootable?
Merely formatting the Windows partition won't have any effect on Grub. Grub is in the master boot record (MBR), and its files like menu.lst are in your Ubuntu partition; you should be just fine. :)

---

### Post by izzmit on 2008-09-22
So, I formatted the windows partition, and can no longer select what OS to boot into. 
Now it just goes straight into Win XP
Now I assume I have an unaccessable but perfectly usable linux install on the other partition?

What can I do to access it?

:(

---

### Post by caljohnsmith on 2008-09-22
> **izzmit said:**
> So, I formatted the windows partition, and can no longer select what OS to boot into. 
Now it just goes straight into Win XP
Now I assume I have an unaccessable but perfectly usable linux install on the other partition?

What can I do to access it?

:(

Merely formatting the Windows partition should not affect Grub in the master boot record (MBR). Did you reinstall Windows? That would have done it. Anyway, probably all you need to do to get Grub back is boot your Live CD, and do the following from a terminal (applications > accessories > terminal):
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know how it goes.

---

### Post by izzmit on 2008-09-22
Yes, i reinstalled windows. :/


What does this mean?
I dont want to kill my windows boot, so I assume I need
to give one partition priority?

```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```

---

### Post by caljohnsmith on 2008-09-22
What you'll need to do is add Windows to your Grub menu so that you can boot either Windows or Ubuntu, or at least that is the easiest way of doing it. From your Live CD, open a terminal, and please post the following:
```
sudo fdisk -lu
```
If you post the above, I can give you more specific instructions of how to do everything.

---

### Post by izzmit on 2008-10-14
**Nevermind, figured out what you were talking about above. Solved. Thanks!**

Disk /dev/hda: 120gb, 120034123776 Bytes
255 Heads, 63 sectors/track, 14593 cylinders, total 234441648
Units = sectors of 1 * 512 = 512 bytes
Disk IDentifier: 0x20352034
Boot: /dev/hda1 Start: 63 End: 200700044 Blocks 100349991 ID: 7 System: HPFS/NTFS

/dev/hda2 Start: 200700045 End:234436544 Blocks: 16868250 ID: f System: W95 Ext'd (LBA)

/dev/hda5 Blocks: 2562336 ID: 82 System: Linux Swap/Solaris

/dev/hda6 Blocks: 14305851 ID: 83: System: Linux

---

