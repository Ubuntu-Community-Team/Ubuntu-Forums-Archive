---
title: "Can't install grub2"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by danageis on 2010-05-29
I recently tried installing the latest stable ubuntu netbook 10.04 on my hp mini 110, and it won't allow me to install GRUB.

What I want to do is install GRUB2 to the Ubuntu partition so I can chainload it, but when I click 'Advanced' on the last install page and select the new ubuntu partition, the 'OK' button is greyed out.

My system is kind of strange, but with previous versions of Ubuntu (even 10.04 betas) it has let me install grub to the ubuntu partition:

sd1 - NTFS Windows 7
sd2 - Extended
.    sd5 - FAT32 Windows XP
.    sd6 - linux swap
.    sd7 - EXT4 Ubuntu 10.04 (have also tried ext3)
sd3 - HFS+ OS X Leopard

Like I said, in the past the ubuntu installer has had no problem with me putting GRUB2 on the ubuntu partition, any suggestions?

My only thought would be that maybe I should try putting the ubuntu partition outside of the extended partition, would that matter?

---

### Post by kansasnoob on 2010-05-29
The only solution I can think of is to choose not to install grub at all. On the same screen where you can select where to install grub there's a box you can uncheck to NOT install any bootloader.

Then after installation use the "grub-setup --force /dev/sdXY" command in a chroot something like this:

```
sudo mount /dev/sdXY /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-setup --force /dev/sdXY
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Of course the XY is generic, X must be replaced with the proper drive designation, and Y with the proper partition designation.

---

### Post by kansasnoob on 2010-05-29
Something that concerns me, this makes me think you may not understand drive and partition designations:

> sd1 - NTFS Windows 7
sd2 - Extended
. sd5 - FAT32 Windows XP
. sd6 - linux swap
. sd7 - EXT4 Ubuntu 10.04 (have also tried ext3)
sd3 - HFS+ OS X Leopard

Drives are designated as /dev/sda, /dev/sdb, /dev/sdc, etc. the last letter indicates the drive number, eg:
/dev/sda = drive #1
/dev/sdb = drive #2
/dev/sdc = drive #3

Partititions are designated with a number following the drive designations, eg:
/dev/sda1 = drive #1/partition #1
/dev/sda2 = drive #1/partition #2
/dev/sdb1 = drive #2/partition #1

---

### Post by danageis on 2010-05-29
Ya, I do not know the correct nomenclature for drives in linux, however all that I listed are partitions on my only hard drive.

It will let me install without grub, and that is what I have done, but how can I open a linux terminal after installation? Should I just type the commands you mentioned in the live CD environment, or is there someway to boot to Ubuntu without GRUB installed after installation?

The only other thing is, why on earth does the Ubuntu installer not want me to install GRUB to the linux partition in the first place??

EDIT: Also, since you seem to be very knowledgeable with GRUB and Ubuntu, I was wondering if you could maybe clarify whether or not I could use GRUB as my primary bootloader rather than Windows Boot Loader. The problems I have faced in the past with GRUB2 are regarding OS X and Windows XP.

GRUB2 finds OS X automatically, but when I try to boot into it from GRUB it would result in a code dump.

I think the problem with Windows XP stems either from the fact that it is on a FAT 32 partition or that it resides inside an extended partition. Regardless, when I have used GRUB2 in the past it has not even recognized my Windows XP partition (Even in the Ubuntu installer it lists it as a FAT32 partition, not as a Windows XP partition)

DO you know of anyway around these problems? Because in reality I would much rather use GRUB that MBR

---

### Post by danageis on 2010-05-30
I gave up on trying to get GRUB to do what I want :/ I tried not installing it and it wouldn't let me install through the terminal either... now I have GRUB in MBR and it boots into Windows 7 fine, has two entries for OS X (32 + 64 bit), and neither of them load, and it hasn't even put my XP partition into the loader... any suggestions?:(

---

### Post by darkod on 2010-05-30
Yes, the commands kansas typed should be run from terminal in live mode.

You can't boot XP from logical partition directly. It would have to have its boot files combined on the win7 partition in that case. So you would still have one entry in grub menu, win7 loader. And selecting that will then show you windows bootloader options for 7 and XP.

I'm not sure how grub2 works with OSX. I know nothing about it. Usually grub2 would only chainload (in other words pass on the boot process) to the OSX loader. That's what it does with windows.

So, are you sure your OSX loader process is fine?

---

### Post by danageis on 2010-05-30
> **darkod said:**
> Yes, the commands kansas typed should be run from terminal in live mode.

You can't boot XP from logical partition directly. It would have to have its boot files combined on the win7 partition in that case. So you would still have one entry in grub menu, win7 loader. And selecting that will then show you windows bootloader options for 7 and XP.

I'm not sure how grub2 works with OSX. I know nothing about it. Usually grub2 would only chainload (in other words pass on the boot process) to the OSX loader. That's what it does with windows.

So, are you sure your OSX loader process is fine?

Ya, that is what I have done... everything works ok now, I have both windows partitions booting from the windows bootloader chained from grub, and Ubuntu boots fine as always. OS X was hard to figure out, by default grub had made an incredibly long entry that did not work. After researching online I found that all that was needed was:

```
menuentry "Apple Macintosh OS X Leopard 10.5.8" {
	insmod hfsplus
	set root='(hd0,3)'
	multiboot /boot
}
```

Any idea on what this means? 0.o

---

### Post by darkod on 2010-05-30
More or less:

menyentry - the name of the entry in boot menu
insmod - module for the filesystem to load, you needed hfsplus, Apple filesystem
root - your OSX partition
multiboot - the bootloader file to call, obviously for OSX that is /boot

---

