---
title: "LVM, GRUB2 and whole disk boot"
date: 2015-06-19
forum: Installation &amp; Upgrades
---

### Post by jeu on 2015-06-19
Ubuntu 14.04.2 LTS on a HP N54L

My existing layout is a LVM on a parition as per default Ubuntu install.

[INDENT]sdd                    8:48   1    29G  0 disk   
&#9492;&#9472;sdd1                 8:49   1  28.9G  0 part   
  &#9492;&#9472;root-root (dm-0) 252:0    0  28.9G  0 lvm   /
[/INDENT]


Trying to move my disk to bigger one following process described [here]("http://askubuntu.com/questions/161279/how-do-i-move-my-lvm-250-gb-root-partition-to-a-new-120gb-hard-disk") (pvcreate, vgextend, pvmove, update-grub, grub-install). 

On the new disk I decided to use "whole disk" lvm i.e without partitions. All documentation say this should work. Even though most examples on the net actually create paritions anyway.

Everything up to update-grub work fine. However, grub-install fail.

First I try:

> grub-install /dev/sdc

*grub-install: error: unable to identify a filesystem in hostdisk//dev/sdc; safety check can't be performed.*

Then:

>grub-install -s /dev/sdc

*error: embedding is not possible, but this is required for RAID   and LVM install*


Searching on the topic seem many others have various issues with LVM/GRUB2 and mostly the advise back is to create partitions and not to use "whole disk" for LVM.

What am I missing here? Is this supposed to work or not, and if so how do I install GRUB2 on a "whole disk" lvm?

---

### Post by dino99 on 2015-06-20
maybe run a > sudo blkid to check the real paths naming

---

### Post by jeu on 2015-06-23
> **dino99 said:**
> maybe run a  to check the real paths naming

Can you explain what I should run that against?

If I run the GRUB to target any disk with a partition on it, it work (and boot successfully of that disc). It is only if the disk has no partitions (MBR/GPT), as is the case with whole disk LVM, that it refuse to install. Currently as a workaround I have a small USB thumb drive with a partition and GRUB on to be able to boot.

It really seems to be a GRUB2 failure/bug/limitation of some sort. GRUB2, as far as I understand, may warn that is not a good idea, but should still install on an non partitioned disk. However, at least in the Ubuntu version, it error in this situation and refuse to install making it not quite 100% compatible with LVM.

---

### Post by oldfred on 2015-06-23
Embedding is where grub converts to blocklists and indicates you are not normally installing it correctly. Block list installs are used where you force install to a partition's boot sector which is only for cases where you have another grub really booting system, or forcing install on a gpt partitioned drive without a bios_grub partition.

Post this, will only show partitions outside LVM, should be /boot & LVM:
sudo parted -l

Generally easier just to do a new install and copy data to new install. If you copy /home you have ally your settings. If you had a lot of applications you manually added you can export a list of installed apps and reinstall those. List is everything and long, but only those not part of default app are then installed.

---

### Post by jeu on 2015-06-25
> indicates you are not normally installing it correctly.

If doing according to what it states is possible, why is it then incorrect to do so? What is the right way then?

> Generally easier just to do a new install and copy data to new install. If you copy /home you have ally your settings. If you had a lot of applications you manually added you can export a list of installed apps and reinstall those. List is everything and long, but only those not part of default app are then installed.

I won't need to re-install. with LVM I can move it partitioned disk if want to. That is one of the design principles behind it.

---

### Post by oldfred on 2015-06-25
Are you trying to install grub to a partition?
Or are you installing to a gpt partitioned drive without a bios_grub partition?

---

### Post by jeu on 2015-06-26
> **oldfred said:**
> Are you trying to install grub to a partition?
Or are you installing to a gpt partitioned drive without a bios_grub partition?

No partitions on the disk at all. LVM installed to whole disk. I did leave space for GRUB (dataalignmentoffset of 2048 sectors).

---

### Post by oldfred on 2015-06-26
Do not know how to install grub to LVM only drive.

Most that have posted with LVM have chosen full drive encryption which also has a separate /boot, so then grub install is normal.

---

### Post by jeu on 2015-06-29
> **oldfred said:**
> Do not know how to install grub to LVM only drive.

Most that have posted with LVM have chosen full drive encryption which also has a separate /boot, so then grub install is normal.

I'm trying to figure out how to install it. What I thought would work clearly didn't.

Your observation is correct about the encrypted drives. Though this is not the case here i.e. not encrypted. I am trying to use "whole disk" though without setting up any MBR type partition.

LVM was installed by:
[INDENT][COLOR=#0000ff]pvcreate --dataalignmentoffset 2048s /dev/sdc[/COLOR][/INDENT]

Then Grub was (attempted) to install based on various methods described online. This is the latest one I tried:
[INDENT][COLOR=#0000ff]grub-install  -s --force /dev/sdc[/COLOR][/INDENT]

---

### Post by xen3 on 2016-05-08
[https://lists.gnu.org/archive/html/grub-devel/2016-05/msg00010.html](https://lists.gnu.org/archive/html/grub-devel/2016-05/msg00010.html)

If you add deb-src for "main" (and possibly updates) you can download the grub source via:

```
apt source grub2
```

This will download, extract, and apply Ubuntu specific patches.

The attachment to the email will allow you to patch Grub before compiling it and installing it.

Install bison, flex and libdevmapper-dev, and automake

```
apt install bison flex libdevmapper-dev automake

```
You will need to symlink automake 1.15 to 1.14:

```
cd /usr/bin
ln -s automake-1.15 automake-1.14
ln -s aclocal-1.15 aclocal-1.14
```

Then go into the source directory, and apply the patch:

```
patch -p0 < patch-file.patch
```

Then run ./configure && make && make install.

It will install in /usr/local. To run it you will need to explicitly do: /usr/local/sbin/grub-install.

You can install additional packages before configure:

```
apt install unifont libfuse-dev libusb-dev libfreetype6-dev
```

And maybe get more features, I don't know. You should be getting grub-mount and grub-mkfont now.

[ This is for Ubuntu 16.04 ].

---

