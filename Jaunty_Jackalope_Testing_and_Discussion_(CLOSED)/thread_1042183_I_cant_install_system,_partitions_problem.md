---
title: "I cant install system, partitions problem"
date: 2009-01-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by goompas on 2009-01-17
Hi
I have problem with new system install 9.04 alpha 3
I have windows vista with ntfs fs and recovery partition with fat32. When i install alpha 3 after step 8 instalator try format partitions and back to partitioning program in step 5. This is when i try use ext4 as logical partition and swap. These same problem i have when try ext3.
I try ubuntu 9.04 alpha3
kubuntu 9.04 alpha3
daily builds
#  20090116.1/
# 20090116.3/

and none work

Work only 200901120090116.1 with ext3

---

### Post by SlowJet on 2009-01-17
> **goompas said:**
> Hi
I have problem with new system install 9.04 alpha 3
I have windows vista with ntfs fs and recovery partition with fat32. When i install alpha 3 after step 8 instalator try format partitions and back to partitioning program in step 5. This is when i try use ext4 as logical partition and swap. These same problem i have when try ext3.
I try ubuntu 9.04 alpha3
kubuntu 9.04 alpha3
daily builds
#  20090116.1/
# 20090116.3/

and none work

Work only 200901120090116.1 with ext3

The Grub can not read ext4 so you need a
/boot ext3, / ext4, /home ext4, and a swap.
That is 4 partitions and you have 2 already  for visa so

sda3 /boot ext3 256MB  
sda4 extended
sda5 / ext4 16384MB
sda6 /home ext4 (the rest minus 2048MB for swap)
sda6 swap swap 2048MB

You can do that easily with the manually partitioner in the installer.
Make sure you indicate size(MB) type, format, and mount point.

g/l

SJ

---

### Post by Slug71 on 2009-01-17
> **SlowJet said:**
> The Grub can not read ext4 so you need a
/boot ext3, / ext4, /home ext4, and a swap.
That is 4 partitions and you have 2 already  for visa so

sda3 /boot ext3 256MB  
sda4 extended
sda5 / ext4 16768MB
sda6 /home ext4 (the rest minus 2048MB for swap)
sda6 swap swap 2048MB

You can do that easily with the manually partitioner in the installer.
Make sure you indicate size(MB) type, format, and mount point.

g/l

SJ

Ahhh, grub CAN boot Ext4!!

The installer is having some issues lately.

---

### Post by goompas on 2009-01-17
> **SlowJet said:**
> The Grub can not read ext4 so you need a
/boot ext3, / ext4, /home ext4, and a swap.
That is 4 partitions and you have 2 already  for visa so

sda3 /boot ext3 256MB  
sda4 extended
sda5 / ext4 16384MB
sda6 /home ext4 (the rest minus 2048MB for swap)
sda6 swap swap 2048MB

You can do that easily with the manually partitioner in the installer.
Make sure you indicate size(MB) type, format, and mount point.

g/l

SJ
Thx but this is not problem with grb but with installer

---

### Post by Slug71 on 2009-01-17
> **goompas said:**
> Thx but this is not problem with grb but with installer

Yes it is, I'd wait a couple days or try todays Daily Build and see if it works.

---

### Post by SlowJet on 2009-01-17
> **Slug71 said:**
> Ahhh, grub CAN boot Ext4!!

The installer is having some issues lately.

The installer is fine for Alpha 3 and grub can not use ext4 after  an extent is created.


SJ

---

### Post by autocrosser on 2009-01-17
Sorry slow_jet---Colin patched grub to use EXT4--a large number of us already boot EXT4 with grub--My system has been converted/installed with EXT4 & I just installed Alpha 3 last night as EXT4 & legacy grub with extents enabled.

---

### Post by SlowJet on 2009-01-17
> **autocrosser said:**
> Sorry slow_jet---Colin patched grub to use EXT4--a large number of us already boot EXT4 with grub--My system has been converted/installed with EXT4 & I just installed Alpha 3 last night as EXT4 & legacy grub with extents enabled.

Well, I'll be a draned.

So has he sent the patch upstream? A few million other people would like to use it. :)

SJ

---

### Post by autocrosser on 2009-01-17
It is in the current grub from the Jaunty repo--I have grub installed on a EXT4 & use it to boot both of my Jaunty/EXT4 installs as well as my backup Intrepid/EXT3 install---The world is very good right now:)

---

### Post by autocrosser on 2009-01-17
Take a look at some "fun" Colin & I had:  [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/316872](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/316872)

Not sure if he went upstream with the patch--I tend to think that he wants a bit more testing first.....

---

### Post by agurk on 2009-01-17
I believe I had the same problem installing alpha 3 in Virtualbox 2.1.0, the alternate CD worked fine though.

---

