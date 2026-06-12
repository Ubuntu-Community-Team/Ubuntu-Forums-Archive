---
title: "External HDD + Grub2 + Win7setup.iso"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by Briksins on 2011-01-08
Hello there!
first of all im sorry for making another thread about the same, i read a lot of simular topic on this forum, the best, which one helped me very much is [this post ]("http://ubuntuforums.org/showpost.php?p=9831791")of "**oldfriend"** 

I'm new to the linux and spend already 2nd day on this simple task, which can be completed within 1h by some guru, anyway... im stuck, please can anyone help me?

Idea/Task:
to make from 1TB external HDD bootable hard with:
1) ubuntu (20GB + 4096MB swap are)
2) Win7 setup (install Win7 OS **from, **not **to** External HDD - to any PC trough USB )  iso size 3.87Gb (Win7 Ult x32/x64 Eng/Ru)
3) rest of the disk - DATA, any files,programs,music....  (NTFS)

I got so far 4 partitions so:

/dev/sda1 - ubuntu 10.10
/dev/sda2 - extended (for swap area)
/dev/sd3 - DATA (ntfs)
/dev/sd5 - swap

I install GRUP2, successfully and its working fine!, it is installed on /dev/sd3 (NTFS) 
cause i want to boot *.ISO's and they are located on DATA partition

when i load GRUB and type in CL ls -l
im getting this:
```

Device hd0: partition table
hd0,msdos5: unknown filesystem //that's probably extended for swap
hd0,msdos3: Filesystem type ntfs - label "ExternalHDD" UUID *******l
hd0,msdos1: Filesystem type ext2 - lable "Ubuntu" last mod. time *** UUID ***blah-blah***

```I create folder "isos" in /boot/isos, according to partition names it is (hd0,msdos3)
so i find grup.cfg and add fallowing:
```

menuentry "Install Windows 7" {
set isofile="(hd0,msdos3)/boot/isos/windows7/win7.iso"
loopback loop $isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile  quiet splash noprompt --
initrd (loop)/casper/initrd.gz
}

```but when im trying to boot it im getting 3 errors:
> File not found
no such disk
you need to load kernel first

press a key to continuePlease can you help me where im wrong? is it problem in the code in cfg file?
or GRUB doesn't support Windows installation bootable .iso file? 

thnak you very much in advance!!!

---

### Post by Briksins on 2011-01-08
ok, looks like i find solution! as far as i see GRUB doesnt support DVD's
and my windows7setup.iso is exactly dvd.iso cause it Win7 Ultimate x32/x64 Eng/Rus and size about 4GB
so reformat my whole drive once more and go other way arround, first of all i create 4GB partition, make it bootable and copy there my windows setup files
after i create another partition for 20GB for Ubuntu + 1 more partition 1GB for swap

now im installing again ubuntu, and after will install grub which supose to detect my win7setup bootable partition automatically :)
so ill gate what i want, Ubuntu+Win7setup trough nice Grub menu :)

there only one more problem, each time ill insert device it will detect win7setup partition, so in win will appear 2 device, but i dont want that! is there any chance i could hide it?

is it possible to make bootbale partition as hidden since GRUB have all details and know how to call it?

---

