---
title: "[SOLVED] Install Second XP OS without losing MBR"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by gaylapdancer on 2007-11-23
Okay, a slightly weird problem.

I have 2 HDDs. a 160gb one and a 320gb one. the 160 is my 'Adonis' partition which contains a bogged up XP Install. the 320 is currently my 'Apollo' Kubuntu partition. 

Ok, What I want to do:

Shrink 320gb partition to 300gb and add 20gb fat32 partition.
Install XP Professional onto this 20gb partition
Add this new OS into my GRUB entry as "Blender"

Now the first 2 I can do (GParted etc), but the third will be interesting as XP wipes the mbr on install.

How can I keep the GRUB in the mbr, and add an entry the new "Blender" OS?

Any help is appreciated

---

### Post by Craigus on 2007-11-23
Some discussion here:

[http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/]("http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/")

---

### Post by gaylapdancer on 2007-11-23
Thanks for the Reply

"If you are going to need to use a Live CD to recover the backup MBR then you could have booted into rescue mode from the install CD (of any linux distro you choose) and mounted the linux partition, chrooted to the root partition and typed grub-install /dev/hdx.

mkdir /mnt/temp
mount /dev/hda3 /mnt/temp ## if hda3 was the linux partition
chroot /mnt/temp
grub-install /dev/hda

That would install the grub first stage boot loader to you the MBR of the hard disk and presented you with the same options you had before the Windows reinstall. no need for backup MBR records!"

Would that work on Ubuntu? and how would I find where GRUB was installed? will the grub-install automatically detect available OSes or would I have to manually enter them?

---

### Post by Craigus on 2007-11-23
> Would that work on Ubuntu? 

I don't see why not.

> and how would I find where GRUB was installed?

Well, that depends where you put it. Presumably it's on the MBR of your primary drive.

>  will the grub-install automatically detect available OSes or would I have to manually enter them?

I think it will.

Another alternative is Supergrub:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#introduction]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#introduction")

---

### Post by gaylapdancer on 2007-11-23
Thanks Mate. 

SuperGRUB looks like a really good tool. I've resized the partition with no hitches, and I'll install and write back with some results! :) Thanks again.

---

### Post by gaylapdancer on 2007-11-23
Install went perfectly and SuperGRUB fixed up Grub straight off. Thanks for the help Craigus :)

---

