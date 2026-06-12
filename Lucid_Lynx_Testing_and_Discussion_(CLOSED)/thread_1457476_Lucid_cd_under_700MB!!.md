---
title: "Lucid cd under 700MB!!"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2010-04-18
I was glad to see that the Lucid daily download is only 694MB :P
There has been alot talk about it being over 700MB and 'overburning' etc.
Thanks.

---

### Post by forcecore on 2010-04-18
just curious why that happens sometimes in daily iso files, do squashfs packs wrong or there will be left some package rotten in iso???

---

### Post by VMC on 2010-04-18
I noticed that todays daily-live had less mega bytes than yesterdays. Its a non issue for me, I only use DVD-RW's.

 Lately though, I have been using usb-creator to install on my flash drive or usb hard drive. I stopped using DVD-RW's.

---

### Post by MacUntu on 2010-04-18
I never understood why they don't do a basic install that easily fits on a CD and one where they don't have to discuss about every byte.

---

### Post by IndyGunFreak on 2010-04-18
> **MacUntu said:**
> I never understood why they don't do a basic install that easily fits on a CD and one where they don't have to discuss about every byte.

I tend to agree... If they want to make a useable OS..Put a *few* apps on the Live CD(Firefox, Empathy and a few others) and focus on things to make sure all hardware works properly.

Personally, I have no way to burn DVD's here at the compound, and one of my machines will not boot USB.. so it's CD or bust for me. :)

---

### Post by VMC on 2010-04-18
> **IndyGUnFreak said:**
> ...one of my machines will not boot USB.. .

Even if your BIOS can't boot from USB, grub2 might be able too.

with a usb drive plugged in do a 'sudo fdisk -l' to get the correct drive info then put the iso on the usb drive and add this menuentry (X,Y is from fdisk info):

```
menuentry "Ubuntu Live" {
loopback loop (hdX,Y)/lucid-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/lucid-desktop-i386.iso --
initrd (loop)/casper/initrd.lz
}
```

---

### Post by IndyGunFreak on 2010-04-18
> **VMC said:**
> Even if your BIOS can't boot from USB, grub2 might be able too.

with a usb drive plugged in do a 'sudo fdisk -l' to get the correct drive info then put the iso on the usb drive and add this menuentry (X,Y is from fdisk info):

```
menuentry "Ubuntu Live" {
loopback loop (hdX,Y)/lucid-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/lucid-desktop-i386.iso --
initrd (loop)/casper/initrd.lz
}
```

Hmm, I'd heard Grub2 might have this capability... 

Do I just copy/paste the ISO onto the thumb drive, or do I have to unpack it.. or should I use a program like unetbootin to setup the drive?...

Thanks.. I'm interested in trying this... also, am I correct in assuming I add that entry to /etc/default/grub ?

---

### Post by VMC on 2010-04-18
> **IndyGUnFreak said:**
> Hmm, I'd heard Grub2 might have this capability... 

Do I just copy/paste the ISO onto the thumb drive, or do I have to unpack it.. or should I use a program like unetbootin to setup the drive?...

Thanks.. I'm interested in trying this... also, am I correct in assuming I add that entry to /etc/default/grub ?

Just copy the iso to the usb drive.

Then add the menuentry to 40_custom. Then run ```
sudo update-grub
```

---

### Post by IndyGunFreak on 2010-04-19
Hmm, I think I'm going it right...but its not working... Below is all relevant info I think.. Do you see anything wrong, or is this just not gonna work w/ my PC?

fdisk -l (sdb is my thumb drive, formatted as ext4)
 
```
ken@ken-desktop:~$ sudo fdisk -l
[sudo] password for ken: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2fdc2fdc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            4500       30401   208057815    7  HPFS/NTFS
/dev/sda2               1         304     2441848+  82  Linux swap / Solaris
/dev/sda3   *         305        4499    33695744   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2002 MB, 2002747392 bytes
255 heads, 63 sectors/track, 243 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0bcd68e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         243     1951866   83  Linux
ken@ken-desktop:~$ 

```

my /etc/grub.d/40_custom...
```
menuentry "Ubuntu Live" {
loopback loop (sdb,1)/ubuntu-10.04-beta1-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-10.04-beta1-desktop-i386.iso --
initrd (loop)/casper/initrd.lz
}
```

Finally, when I update grub, I'm "assuming" it should recognize the ISO on my thumb drive, but it doesn't
```
ken@ken-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
ken@ken-desktop:~$ 

```

When I boot the grub menu, the entry is there, but if I select Ubuntu Live, I get a message saying that I have to load the kernel first.

Thanks..
IGF

---

### Post by VMC on 2010-04-19
> **IndyGunFreak said:**
> 
my /etc/grub.d/40_custom...
```
menuentry "Ubuntu Live" {
loopback loop (sdb,1)/ubuntu-10.04-beta1-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-10.04-beta1-desktop-i386.iso --
initrd (loop)/casper/initrd.lz
}
```

When I boot the grub menu, the entry is there, but if I select Ubuntu Live, I get a message saying that I have to load the kernel first.

For some reason grub doesn't like the nomenclature **(sdb,1**).
Try using **(hd1,1)** instead.

---

### Post by Starks on 2010-04-19
[https://wiki.ubuntu.com/UnitsPolicy](https://wiki.ubuntu.com/UnitsPolicy)

Figured I should post this.

---

### Post by mcduck on 2010-04-19
> **Starks said:**
> [https://wiki.ubuntu.com/UnitsPolicy](https://wiki.ubuntu.com/UnitsPolicy)

Figured I should post this.

+1 to this, as the disk image has been small enough to fit a standard CD (wihtout overburning) for most of the time of Lucid's development. :D

---

