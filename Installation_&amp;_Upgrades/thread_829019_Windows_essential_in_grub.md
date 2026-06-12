---
title: "Windows essential in grub"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by oyankee on 2008-06-14
Hi everybody,
I just installed Win Essential and repaired grub. But now I can't load Wins from grub.
fdisk -l
> Disk /dev/hda: 40,0 GB, 40*007*761*920 bajt&#367;
hlav: 255, sektor&#367; na stopu: 63, cylindr&#367;: 4*864
Jednotky = cylindry po*16065 * 512 = 8*225*280 bajtech
Identifikátor disku:&#8239;0x000abe09

Za&#345;ízení Zavád&#283;t   Za&#269;átek       Konec    Bloky    Id  Systém
/dev/hda1               1        4023    32314716   83  Linux
/dev/hda2   *        4024        4788     6144862+   c  W95 FAT32 (LBA)
/dev/hda3            4789        4864      610470    f  W95 Roz&#353;. (LBA)
/dev/hda5            4789        4864      610438+  82  Linux swap/Solaris


menu.lst
> ## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=48829db4-84de-4cef-8ac9-f283c6acf222 ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=48829db4-84de-4cef-8ac9-f283c6acf222 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=48829db4-84de-4cef-8ac9-f283c6acf222 ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=48829db4-84de-4cef-8ac9-f283c6acf222 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title Microsoft Windows ;
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1


Can anyone help, please? thank you

---

### Post by ChameleonDave on 2008-06-14
What is Win Essential?

What happens when you try to boot?

---

### Post by dacorr on 2008-06-14
which partition is windows on?

Dac

---

### Post by zvacet on 2008-06-14
Chanfe your win entries and the they should look like this

title Microsoft Windows ;
rootnoverify (hd0,1)
chainloader +1
 
save an close the file.After rweboot you should be able to boot in windows.

---

### Post by oyankee on 2008-06-14
Thanks, it didn't help. They are XP Pro on hda2, ubuntu is on hda1. So it's good with hd0,1, isn't it? When I try to boot nothing happens. Just blinks and stay at grub.

---

### Post by meierfra. on 2008-06-14
> So it's good with hd0,1, 
Yes.


Boot from your Windows CD. At the first screen press "r" to enter the repair console and type

```
fixboot
```

Hopefully this fixes your problem (but I'm not sure). 
(In case that you boot directly into Windows, you have to reinstall Grub again).


If this did not cure your problem:

Are you able to access your Windows partition from Ubuntu? (Go to Places->Computer. One of those icons should be for Windows).

---

### Post by meierfra. on 2008-06-14
Did you ever try  "root (hd0,1)" in place of "rootnoverify (hd0,1)"

---

### Post by oyankee on 2008-06-14
> **meierfra. said:**
> Did you ever try  "root (hd0,1)" in place of "rootnoverify (hd0,1)"

Yes, no results. I'll try fixboot as you advise. Now I am able to get to the partition from ubuntu. It was shutted down corectly.

---

### Post by VMC on 2008-06-14
It appears your Start & End overlap between W95 and Swap:

/dev/hda3 4789 4864 610470 f W95 Roz&#353;. (LBA)
/dev/hda5 4789 4864 610438+ 82 Linux swap/Solaris

---

### Post by meierfra. on 2008-06-14
> it appears your Start & End overlap between W95 and Swap:

/dev/hda3 4789 4864 610470 f W95 Rozš. (LBA)
/dev/hda5 4789 4864 610438+ 82 Linux swap/Solaris

hda3 is just an extended partition containing hda5. So this is normal.

---

### Post by oyankee on 2008-06-15
Hm, fixboot didn't help.

---

### Post by meierfra. on 2008-06-15
Are you getting any error messages, when trying to boot  XP?

You might try to run "chkdsk" from the recovery console of the Windows  CD.

---

### Post by oyankee on 2008-06-15
No,I already tried that. And I wish I got any messages. But nothing happens. It just blinks. Is it possible that ntloader is broken?

---

