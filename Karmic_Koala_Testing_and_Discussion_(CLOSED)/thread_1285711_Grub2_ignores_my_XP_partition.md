---
title: "Grub2 ignores my XP partition"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bgenc on 2009-10-08
I have the following disk structure:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbdc0d876

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496   83  Linux
/dev/sda2            3648       19457   126993825    5  Extended
/dev/sda5            3648        3890     1951866   82  Linux swap / Solaris
/dev/sda6            3891        8753    39062016   83  Linux
/dev/sda7            8754       16888    65344356   83  Linux
/dev/sda8           16889       19457    20635461    7  HPFS/NTFS

```

XP resides in /dev/sda8 under a logical partition. Ubuntu is in /dev/sda1. Is it possible to add XP to grub2 menu? By the way, I don't even see a menu during start up.

---

### Post by wilee-nilee on 2009-10-08
Run sudo update-grub in the terminal it should load it into the grub menu.

---

### Post by taavikko on 2009-10-08
os-prober should help with detecting the XP

menu can be accessed by pressing "shift" during startup.

---

### Post by bgenc on 2009-10-08
> **wilee-nilee said:**
> Run sudo update-grub in the terminal it should load it into the grub menu.

I tried that. It doesn't work:

```

bgenc@bgenc-ubuntu:/etc/grub.d$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-11-generic
Found initrd image: /boot/initrd.img-2.6.31-11-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

---

### Post by bgenc on 2009-10-08
I am looking for a way to create a custom entry for XP in /etc/grub.d/40_custom. Alas, I don't know what must be put into it. The wiki is not helpful as well.

---

### Post by bgenc on 2009-10-08
> **bgenc said:**
> I am looking for a way to create a custom entry for XP in /etc/grub.d/40_custom. Alas, I don't know what must be put into it. The wiki is not helpful as well.

Ok, I guess I found what I have been looking for, sort of.

```

#! /bin/sh -e

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib
echo "Adding Windows" >&2
cat << EOF
menuentry "Windows Vista" {
EOF
save_default_entry | sed -e "s/^/\t/"
cat << EOF
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set q67e48fd884ds522
chainloader +1
} 

```

I found this example, but what is "q67e48fd884ds522"?. Am I supposed to replace it with something? If so, with what?

---

### Post by Rumpty on 2009-10-08
Before you go any further, did you try "sudo update-Grub2" command? It found my Windows partitions ok.

---

### Post by bgenc on 2009-10-08
> **Rumpty said:**
> Before you go any further, did you try "sudo update-Grub2" command? It found my Windows partitions ok.

yes, yes, I tried that as well. 

Now that I have added the above text into 40_custom, I have an entry in the grub menu. However, when I try to boot into XP, I receive a BOOTMGR not found error. Is it because XP is installed in a logical drive and ubuntu formatted the primary partition for itself and somehow wiped the BOOTMGR during the process? Is there any way to force XP to boot? 

Damn, I need this stupid XP thing for my directx class and I don't want to repartition my whole disk just to be able to install it.

---

### Post by alphacrucis2 on 2009-10-08
> **bgenc said:**
> Ok, I guess I found what I have been looking for, sort of.

```

#! /bin/sh -e

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib
echo "Adding Windows" >&2
cat << EOF
menuentry "Windows Vista" {
EOF
save_default_entry | sed -e "s/^/\t/"
cat << EOF
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set q67e48fd884ds522
chainloader +1
} 

```

I found this example, but what is "q67e48fd884ds522"?. Am I supposed to replace it with something? If so, with what?

That is the uuid of the partition. Gparted will tell you what it is but no doubt there is a command line way of listing it.


Edit: blkid will list them

---

### Post by celticbhoy on 2009-10-08
The q67 number is uuid number for the partition, the one you have copied is only applicable to machine it is from. If you run gparted you will get the uuid number for your sda8 and replace.

---

### Post by wilee-nilee on 2009-10-08
> **bgenc said:**
> I tried that. It doesn't work:

```

bgenc@bgenc-ubuntu:/etc/grub.d$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-11-generic
Found initrd image: /boot/initrd.img-2.6.31-11-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

 The code input here looks strange to me /etc/grub.d$ if this a root input; if so try it in a regular terminal. I also notice that the windows partition is the last so if it is the last install then there are ways to get it into grub although I have never had to do that.

---

### Post by taavikko on 2009-10-08
> **celticbhoy said:**
> The q67 number is uuid number for the partition, the one you have copied is only applicable to machine it is from. If you run gparted you will get the uuid number for your sda8 and replace.

No need to run gparted,
you can get the UUID in CLI
```
sudo blkid -c /dev/null |grep sda8
```

---

### Post by bgenc on 2009-10-08
Thanks for the uuid help. I attempted my previous test with the correct UUID of the windows partition but it doesn't help. I have this dreaded BOOTMGR not found error.

---

### Post by bgenc on 2009-10-08
and this is what is in grub.cfg after update-grub:

```

### BEGIN /etc/grub.d/40_custom ###
menuentry "Windows XP" {
insmod ntfs
set root=(hd0,8)
search --no-floppy --fs-uuid --set 62B659922551BCEB
chainloader +1
}
### END /etc/grub.d/40_custom ###

```

---

### Post by VMC on 2009-10-08
Windows doesn't like it when its not first. You have to map it in.
Since your Windows is on the 8th partition try something like this:
```
menuentry "Microsoft Windows XP" {
      drivemap (hd0) (hd8)
      set root=(hd0,8)
      chainloader --force +1
}
```Read all about one guys journey [here]("http://www.mail-archive.com/grub-devel@gnu.org/msg10123.html").

---

### Post by ranch hand on 2009-10-08
I do not run virus' on my box so I don't have Win Jerry Lewis Pro but I think that your problem is there.

I hope you have an install disk for XP.  Your MBR for it is gone.  I would try to recover it.  I do not think it will help.

I would back everything up and format the drive and start over.  Win will be a lot happier on a primary partition and being first on the drive.  I would not waste a lot of space on it, but that is where it should be put.  Then install Karmic again.

If you do not want to do that, you might try reinstalling grub-common and grub-pc.  I have little hope for this either.

I really think that your XP is cooked.  Time to reinstall.  It sounds like the partition structure of you box could do with an update anyway.

---

### Post by bgenc on 2009-10-09
> **VMC said:**
> Windows doesn't like it when its not first. You have to map it in.
Since your Windows is on the 8th partition try something like this:
```
menuentry "Microsoft Windows XP" {
      drivemap (hd0) (hd8)
      set root=(hd0,8)
      chainloader --force +1
}
```Read all about one guys journey [here]("http://www.mail-archive.com/grub-devel@gnu.org/msg10123.html").

Isn't this for when you have two harddrives and windows is on the second one? In my case, I have only one drive which is partitioned into one primary and 4 logical partitions.

---

### Post by cheesypoof on 2009-10-09
Hey bgenc can you post your fstab for me? I had a similar problem with grub2/os-prober not detecting my vista partition.

---

### Post by bgenc on 2009-10-11
> **cheesypoof said:**
> Hey bgenc can you post your fstab for me? I had a similar problem with grub2/os-prober not detecting my vista partition.

I sure can:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a1100aa6-4a79-4e8a-8035-86a59f38883b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=42642035-6470-4f8b-8214-2c938d4fe718 /home           ext3    defaults        0       2
# /storage was on /dev/sda7 during installation
UUID=a58f6971-0071-4703-a92a-018c3f94fb4d /storage        ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=95dff4ee-1e93-4182-a375-5ae032dc404c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Windows XP partition added manualy by bgenc
UUID=62B659922551BCEB /windows	ntfs	defaults	0

```

I added the last line manually after install

---

