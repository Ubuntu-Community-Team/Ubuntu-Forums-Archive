---
title: "Dual boot problem: GRUB error 11"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by koloman on 2007-09-11
I have installed both Xubuntu and Windows XP on the same IDE hard drive, and am now having trouble getting Windows to boot through the GRUB boot menu (Xubuntu, the GRUB default,  starts up just fine). Selecting Windows from the menu just gives me an *Error 11: Unrecognized device string*.

I realize this is the kind of thing which has been dealt with a number of times here already, and I have really tried to find a solution here and using Google but everything thus far has come up short. I've spent the better part of the day on this problem and am already having trouble remembering just which things I've already tried and which not. Any help would be greatly appreciated.

Windows boots up successfully with the [Super GRUB CD]("http://supergrub.forjamari.linex.org/") by selecting *Windows* > *Boot Windows from 2nd Partition (Laptop)*, just not through the GRUB boot menu.

*fdisk -l* gives out this:

```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7692    61785958+  83  Linux
/dev/hda2   *        7693       14405    53922172+   7  HPFS/NTFS
/dev/hda3           14406       14593     1510110    5  Extended
/dev/hda5           14406       14593     1510078+  82  Linux swap / Solaris
```

The appropriate part of */boot/grub/menu.lst* (the only part I have touched besides the *timeout* and *default* parameters) reads like such:

```

title		WinXP
rootnoverify	hd(0,1)
#makeactive
chainloader	+1
boot
```

Can anyone hazard a guess as to what the problem might be?

---

### Post by merlinus on 2007-09-11
You might try this:

title        WinXP
rootnoverify        (hd0,1)
savedefault
makeactive
chainloader    +1

---

### Post by koloman on 2007-09-11
[QUOTE=merlinus]You might try this:[/QUOTE]

Thank your for your prompt reply! Unfortunately I still encountered the same *Error 11* even with the changes you suggested. Any other ideas?

---

### Post by merlinus on 2007-09-11
You might try reinstalling grub, either from supergrub or by booting from the live cd and opening a terminal:

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```

Substitute results from find for (hdx,y) and setup (hdx).

---

### Post by cotcot on 2007-09-11
You do not have windows on the first partition. 
You need to do the map thing to make windows thinking that it is on the first partition. This is what the grub manual says about it :
> 13.3.23 map
&#8212; Command: map to_drive from_drive

Map the drive from_drive to the drive to_drive. This is necessary when you chain-load some operating systems, such as DOS, if such an OS resides at a non-first drive. Here is an example: 
          grub> map (hd0) (hd1)
          grub> map (hd1) (hd0)
     

The example exchanges the order between the first hard disk and the second hard disk. See also DOS/Windows.

You have to add this map ... in the grub menu. Please consult the grub manual for details or ask the menu.list to somebody with the same situation.

Good luck

---

### Post by koloman on 2007-09-11
[QUOTE=merlinus]You might try reinstalling grub, either from supergrub or by booting from the live cd and opening a terminal:[/QUOTE]
I had actually tried this one before. I tried again, but to no avail.

[QUOTE=cotcot]You do not have windows on the first partition.
You need to do the map thing to make windows thinking that it is on the first partition.[/QUOTE]

OK. The GRUB manual seems to talk only of substituting drives, not partitions, but I tried changing my menu.lst to say the following:

```
title		WinXP
map		(hd0,0) (hd0,1)
map		(hd0,1) (hd0,0)
rootnoverify	hd(0,0)
savedefault
makeactive
chainloader	+1
```

This still produced the same *Error 11* after a reboot. I am not quite sure of what I'm doing with my menu.lst the whole time, as I'm sure you can see.

---

### Post by merlinus on 2007-09-11
You can try changing it to this:

title Windows XP
root (hd0,1)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

But mapping is usually for two hard drives....

---

### Post by koloman on 2007-09-11
[QUOTE=merlinus]You can try changing it to this:[/QUOTE]
Thank you, I'll try that tomorrow when I get back home. It's nice to see the kind of support one can get here, you guys have been very quick to help me indeed :)

---

### Post by meierfra on 2007-09-11
merlinus first suggestion :
> 
title WinXP
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1


is   what  should have  worked. You probably noticed,  but I just want to make sure: he used

 (hd0,1)    and not   hd(0,1)

You  used hd(0,0)   and hd(1,0)   various times, as far as I know that this wrong under any circumstances.
Indeed using hd(1,0)  causes error 11: wrong syntax of a device string.

---

### Post by koloman on 2007-09-12
[QUOTE=meierfra]You probably noticed, but I just want to make sure: he used

(hd0,1) and not hd(0,1)[/QUOTE]

You are of course correct, and I had not noticed my typo. Using merlinus' initial suggestion sans typos works, and I feel like an idiot now :/

Thank you so much to all who took the time to help me :)

---

