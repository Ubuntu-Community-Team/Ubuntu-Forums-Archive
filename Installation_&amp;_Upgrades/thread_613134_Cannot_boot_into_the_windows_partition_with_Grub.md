---
title: "Cannot boot into the windows partition with Grub"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by Chrys7 on 2007-11-14
Hello. I know that this has been answered before but I have tried all the suggestions in other postings without any sucess. So here goes...
I reinstalled windows and I cannot access them with Grub. 
I am using Ubuntu Feisty 7.04. 
This is how my hard disk looks:

```

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1950    15663343+   7  HPFS/NTFS
/dev/hda2            1951        7687    46082452+   7  HPFS/NTFS
/dev/hda3   *        7688       12033    34909245   83  Linux
/dev/hda4           12034       12160     1020127+   5  Extended
/dev/hda5           12034       12160     1020096   82  Linux swap / Solaris


```

This is how my /etc/fstab file looks:

```

proc /proc proc defaults 0 0
# Entry for /dev/hda3 :
UUID=bf0bbbd3-6c41-4fe8-8057-26693d916e68 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=80C2F69090FA0800 /media/hda1 ntfs umask=222,utf8 0 1
# Entry for /dev/hda2 :
UUID=D8A4E6BEA4E69E6E /media/hda2 ntfs umask=222,utf8 0 1
# Entry for /dev/hda5 :
UUID=7b76bfd8-55dc-432a-ac48-9fb6e418cd1f none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0

```

This is how my /boot/grub/menu.lst file looks (without the comments):

```


default		1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=bf0bbbd3-6c41-4fe8-8057-26693d916e68 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=bf0bbbd3-6c41-4fe8-8057-26693d916e68 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootverify		(hd0,1)
savedefault
makeactive
chainloader	+1

```

The windows partition is mounted to /media/windows


That's it...

regards

---

### Post by mikewhatever on 2007-11-14
There seems to be a problem in fstab. Any idea why does Windows partition shows as **# Entry for /dev/ !! UNKNOW DEVICE !! :** and not **# Entry for /dev/hda1 :**?

---

### Post by meierfra on 2007-11-14
Are you able to access your windows partitions from feisty?


Did your try to fix the windows boot sectors (either with a windows CD or Supergrub)?

---

### Post by Chrys7 on 2007-11-14
mikewhatever: No ideas why I get that.

meierfra: I have two ntfs partitions. I can read/write the /dev/hda2 parition but I cannot write to the /dev/hda1. I can only read it. This is where I re-installed windows.
I don't want to fix windows paritions with the windows cd because then I won't be able to boot to the ubuntu partition (which I mainly use).
I haven't tried Super Grub. If you don't have any ideas on how I can fix that, I will give it a try.

(Thanks your the responses)

---

### Post by logos34 on 2007-11-14
Looks to me like you need to change a few things:

Delete this entry in fstab:

> [COLOR="Red"]# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=80C2F69090FA0800 /media/hda1 ntfs umask=222,utf8 0 1[/COLOR]

hda1 is mounting at /media/windows, per the last line.

Change the boot flag to hda2:

sudo gparted

Right-click on hda2>manage flags>tick 'boot' box

Also, this line in menu.lst:

> rootverify		(hd0,1)

AFAIK it should be 'root' or root**no**verify'

---

### Post by meierfra on 2007-11-14
I don't think that fixboot overwrites your MBR. It fixes the Windows Boot sector, which is on the first sector of the windows partition. But I'm not a 100% sure that it doesn't touch the MBR. (Edit: I just tested it. "fixboot" does not change the MBR. So it is safe to use)

So  get Supergrub. (It's good to have anyway).  If the windows boot sector is at fault, Supergrub should be able to fix it.

Information on Supergrub:  [Hermanzone]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by meierfra on 2007-11-14
```
rootverify (hd0,1)
```

Good catch. I didn't notice that. That actually  might solve the problem!

(But I never  worry about boot flags. The "makeactive" should take care of it)

---

### Post by Chrys7 on 2007-11-14
> **logos34 said:**
> Looks to me like you need to change a few things:

Delete this entry in fstab:



hda1 is mounting at /media/windows, per the last line.

Change the boot flag to hda2:

sudo gparted

Right-click on hda2>manage flags>tick 'boot' box

Also, this line in menu.lst:



AFAIK it should be 'root' or root**no**verify'

I  did what you said and I get an error message "NTLDR is missing, press ctrl+alt+del to continue".
Also, in gparted are you sure I shouldn't change the hda1 disk to "boot" since that is that is the windows parition? Anyway I tried all these and also changed the values to "root" and "rootnoverify" in the menu.lst file. I still get that error message.
Any more suggestions?

---

### Post by mikewhatever on 2007-11-14
If your Windows installation is on hda1, then the following entry
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd0,1)
savedefault
makeactive
chainloader	+1

should look like this
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(**hd0,0**)
savedefault
makeactive
chainloader	+1

(hd0,0) is the first partition on the HDD, since grub starts counting partitions from zero. It should be (hd0,1) if Windows is on hda2.

---

### Post by Chrys7 on 2007-11-14
> **mikewhatever said:**
> If your Windows installation is on hda1, then the following entry


should look like this


(hd0,0) is the first partition on the HDD, since grub starts counting partitions from zero. It should be (hd0,1) if Windows is on hda2.

Simple as that. Thank you mikewhatever. 
Problem solved!

---

