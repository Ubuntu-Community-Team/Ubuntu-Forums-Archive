---
title: "Hard drive pains."
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by VoiceOvGod on 2007-06-25
I got two SATA Hard Drives, one is from Western Digital, the other Maxtor.

Background: Originally using the Maxtor, then swapped out for the WD. Maxtor still has old (useless) information on it.

I keep trying to add the Maxtor, but when I boot up, my computer tries to read off of both HDs as the Master. I see one set of two pegs on the back of the HD, and I have tried using a jumper on them, but my computer still reads it as a master. This is prolly a hardware or boot issue...

However, once I am in Ubuntu, and I try to modify the disk, it will not allow me to modify it at all (sudo or otherwise). I just want to expand my disk storage, and I just can't access it at all.

---

### Post by nyvalbanat on 2007-06-26
Are you absolutely positive you set the jumpers correctly?

---

### Post by VoiceOvGod on 2007-06-26
The way the back of the Maxtor drive is set up as follows:


[----SATA POWER---][--SATA DATA--]{**}

The section with the two stars is where I think the jumper should go. There is only the two pegs, and I have put a jumper on it, but no luck.

---

### Post by dabl on 2007-06-26
Probably you need to reset the "bootable" flag to "no" on the one that you don't want to boot from.  You'll need something like GParted live CD, or an old DOS disk with FDISK (or a bash shell guru).  Here's where you get the GParted live CD ISO image: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Also, check your BIOS and make sure they are in the correct boot sequence.

---

### Post by VoiceOvGod on 2007-06-26
> **dabl said:**
> Probably you need to reset the "bootable" flag to "no" on the one that you don't want to boot from.(...) 

Also, check your BIOS and make sure they are in the correct boot sequence.


Any suggested resources for the BIOS stuff, or just my hardware documentation that came with the MoBo?

---

### Post by VoiceOvGod on 2007-06-26
And for the record, I do not need the old information. It's just a bunch of useless stuff.:D

---

### Post by logos34 on 2007-06-26
> **VoiceOvGod said:**
> I got two SATA Hard Drives, one is from Western Digital, the other Maxtor.

Background: Originally using the Maxtor, then swapped out for the WD. Maxtor still has old (useless) information on it.

I keep trying to add the Maxtor, but when I boot up, my computer tries to read off of both HDs as the Master. I see one set of two pegs on the back of the HD, and I have tried using a jumper on them, but my computer still reads it as a master. This is prolly a hardware or boot issue...

However, once I am in Ubuntu, and I try to modify the disk, it will not allow me to modify it at all (sudo or otherwise). I just want to expand my disk storage, and I just can't access it at all.

...

Any suggested resources for the BIOS stuff, or just my hardware documentation that came with the MoBo?

Alll SATA drives are 'master' (each has its own dedicated sata channel).  Master/slave is IDE talk.  I don't believe you need the jumpers unless these are SATA 300/SATA II and you need to run them in SATA 150 mode for backward compatibility with your sata controller (some like Hitachi use [firmware update -edit]).  You should be able to choose the first boot drive in the **hard disk boot priority **section of the BIOS.

Check the manufacturer website for documentation.

I think you need to format this drive first (using gparted to make an ext3 parititon for instance) and then create a directory to mount it, adding it to fstab.

---

### Post by VoiceOvGod on 2007-06-26
> **logos34 said:**
> 

I think you need to format this drive first (using gparted to make an ext3 parititon for instance) and then create a directory to mount it, adding it to fstab.


any suggestions as to where to mount the hard drive? I've *always* had problems with mounting. Never can get it to work right.

and what will I have to edit in fstab, specifically?

---

### Post by logos34 on 2007-06-26
**/media** is the standard place.

so it would be** /media/<drivelabel>**

you just add a line to fstab like
**/dev/sda1 /media/sda1 <type>** .....

---

### Post by VoiceOvGod on 2007-06-26
So, I would label it something like /media/sdb1, and then on a line in ftsab it'd be like

**/dev/sdb1    /media/sdb1    ext3**

correct?

---

### Post by logos34 on 2007-06-26
yeah, like this:

**/dev/sdb1 /media/sdb1 ext3 defaults,errors=remount-ro 0 1**

Then create the directory:
**sudo mkdir /media/sdb1**

When you reboot the formatted drive partition should automount there.

Or if you want to use UUID's:

**blkid**

Find your newly formatted partition and add it to fstab thus: 

**UUID=r96b3130-09712-4tcb-b8ce-efgft69a5d6t7 ext3 defaults,errors=remount-ro 0 1**

or it might look like this:

[B]# /dev/sdb1
UUID=r96b3130-09712-4tcb-b8ce-efgft69a5d6t7 ext3 defaults,errors=remount-ro 0 1[/B]

The first way is fine though.

---

### Post by VoiceOvGod on 2007-06-26
:) Cool,

Now I just gotta get it formatted to ext3 from NTFS, so once I get it mounted, I can fdisk it, correct?

Yes, I tried formatting it recently (like an hour ago). DOH!

---

### Post by logos34 on 2007-06-26
> **VoiceOvGod said:**
> :) Cool,

Now I just gotta get it formatted to ext3 from NTFS, so once I get it mounted, I can fdisk it, correct?

Yep, should show up with

sudo fdisk -l

edit: actually fdisk will show all formatted drives and partitions, mounted or not

---

### Post by VoiceOvGod on 2007-06-26
Thank you very much for your help.

It's people like you that really show how wonderful Ubuntu's Community really is.

:KS

---

