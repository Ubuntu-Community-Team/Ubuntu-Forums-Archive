---
title: "Small HDD installation 6.06"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by David_UK on 2007-01-05
* Slightly embarrassed *

Hi.  Playing about with my 6.06 live CD to get a feel for the installation, I tried to install on my old test rig:

AmD Athlon 1000GHz
384RAM
HDD 1 - 13GB IDE FAT32 with Win98SE
HDD 2 - 4GB IDE FAT32 empty (a very old HDD)

Thought I'd try installing on disc 2 and see how the dual-boot works with win98.  Anyway, installation hangs at file copy 22% having selected the 'automatic' settings for partitioning to use all of disc 2.  At this stage there is no response from anything, and I have to reset PC.

Subsequently, fdisk does not recognise HDD 2 at all.  I'd be interested to know if a linux install stops fdisk from seeing the partition, and if so, is there a utility which can restore it to dos-compatible.

Any comments gratefully received....

---

### Post by kidders on 2007-01-05
Hi there,

I can't be sure if it's the cause of your problems, but you really, really, *really* shouldn't be installing Linux on FAT32. Could you post the output of **fdisk -l /dev/hdb** (assuming that's where your second hard disk is), so we can see the error message?

---

### Post by David_UK on 2007-01-06
Hi Kidders

Thanks.  Just to clarify, the partitioner included on the disc ran ok, so I presume the HDD was successfully changed from FAT32 to the linux partitions.  Subsequently linux failed to install.

Er, I'll need to do some research to find out how to run the check you ask for.

---

### Post by kidders on 2007-01-06
> **David_UK said:**
> Er, I'll need to do some research to find out how to run the check you ask for.Sorry... From you're o/p, I assumed you were familiar with fdisk. It doesn't matter.

Perhaps you could try the Ubuntu alternative install. We *could* spend ages trying to figure out what it is about your PC Ubuntu doesn't like ... but on the other hand, the alternative installation might just work for you. :-)

**Edit:** Just to clarify ... Installing Ubuntu shouldn't impact other operating systems' ability to detect hard disks. Having said that, Windoze will not enjoy trying to make sense of non-MS filesystems. It only likes to work with proprietary Microsoft ones.

---

### Post by halw on 2007-01-06
Yes, definetly use alternate cd install on 4 Gb hd. Install from live cd wants swap space. Which when installing to a small hd you will not have much of.

---

### Post by David_UK on 2007-01-06
Thanks Kidders

I'll try moving that HDD 2 to another PC and see if it's recognized - I often find it handy to have spare ones while I'm tinkering.  I'll also check the mobo compatibility with linux (the live cd worked fine, but no sound) and basically try the things I should have done in the first place....

I'm a little more switched on about fdisk now.  When I said it's not recognised by fdisk I meant in DOS.  This is why I am now confused as to why it isn't recognised.  

I gather that linux also has an fdisk command, which I think you are referring to.  Presumably I could run that from the Live CD (because the linux install failed)?

Thanks for your input.

---

### Post by David_UK on 2007-01-07
> **kidders said:**
> Could you post the output of **fdisk -l /dev/hdb** (assuming that's where your second hard disk is), so we can see the error message?

Running that from the live CD, gives: *Unable to open /dev/hdb*
Both HDD's are visible in my computer but of course /hdb cannot be mounted.

I'm not too concerned about being able to install the linux at this stage, but I would be interested to find a utility that would allow the 2nd HDD to be restored to a configuration that would allow it to be visible to windows again (the DOS fdisk cannot see the second drive).

Thanks.

---

### Post by louieb on 2007-01-07
Try the GParted live CD. Don't have link handy just Google GParted. It can format fat32.   Don't know why the live CD install did not work you have plenty  of ram w 384M . 
BTW with Ubuntu live or from hard drive to get something out of fdisk its :```
sudo fdisk -l
```

---

### Post by kidders on 2007-01-08
> **David_UK said:**
> Running that from the live CD, gives: *Unable to open /dev/hdb*That's not good. Did you run the command as root?

Regardless of what's on the hard disk, both Windows and Linux should be able to see it. It's slightly worrying that a disk partitioner belonging to any OS won't recognise the disk for you. :confused:

---

### Post by confused57 on 2007-01-08
```
sudo fdisk -l
```
The -l is a small "L", if that makes any difference?

---

### Post by David_UK on 2007-01-08
> **louieb said:**
> Try the GParted live CD. Don't have link handy just Google GParted. It can format fat32.

Thanks louieb, that might be exactly what I need to recover the HDD for windows use.

---

### Post by David_UK on 2007-01-08
> **kidders said:**
> That's not good. Did you run the command as root?

Sorry Kidders.  I'm not sure what you mean.  I ran the command from the Terminal from the live CD.  I typed: *sudo fdisk -l /dev/hd(a as master, b when slave)*.  

I have now tried setting that small, slave drive as the *master*, which led to this:
1) DOS fdisk can see 2 partitions on it, it can only delete the 1st, non-dos partition.  It can't handle the small extended partition in second place.
2) Linux fails to install as before, becoming hung at 22% of the file transfer stage.

As you say, clearly something is up with the PC's config.  I'll play about some more though and perhaps try a different HDD.

Thanks for your input.

---

### Post by David_UK on 2007-01-08
> **confused57 said:**
> The -l is a small "L", if that makes any difference?

Thanks confused57.  It's one of those things that could so easily be misinterpreted!

---

### Post by David_UK on 2007-01-12
Update:

Have changed the slave HDD and the install of 6.06 went fine.  Thanks for everyone's input.

Have used GPartEd to format the non-compatible HDD back to a single FAT32 partition so I can use it as a windows drive.

The dual boot works fine with win98se on the master drive.

---

