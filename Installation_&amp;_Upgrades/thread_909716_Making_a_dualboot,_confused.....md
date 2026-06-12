---
title: "Making a dualboot, confused...."
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by Bommetje on 2008-09-03
Hi,

I'm trying to make a dualboot on my system with Windows XP pro SP3 and Ubuntu 8.04.
I read different tutorials about how to do it but i'm kind of confused and hope you can help out.

According to several tutorials I read it says that during the part of the ubuntu installation where I should pick a partition I should pick Guided - resize partition, and it should recognise my WinXP partition, problem is I don't see this option at all.

So what i did is resize my partition in WinXP.
My WinXP partition was 200gb and I resized it too 160gb and left the 40gb unallocated.

Now when I get to the part of the Ubuntu installation where I should choose a disk, I pick manual but after that I'm at a loss at what to do.

Any help would be greatly appreciated.

---

### Post by thesurgeon on 2008-09-03
You shouldn't have to manually do anything mate. Change the partition back to 200Gb for the XP partition and go through the setup again. It should prompt you to resize the partition, It s really not confusing at all, its probably just because your not used to it. When you've done it once you'll find it much easier. My Linux box is in the shed and its to late to get otherwise I'd of wrote a guide for you. 

I would of left the partition at 200Gb and gone through the setup again. 

Does it actually see the NTFS partition? What options are available to you? What type of Drive is it? Does it actually see the HDD or is it a SATA drive as theres sometimes issues installing operating systems when using some SATA drives then its a case of going into the BIOS and changing SATA support to disabled or compatibility mode obviously depends on the type of BIOS etc etc...

Try putting more information on here just so people can see what you see. Your explination is all we see. Its kinda like getting information from the service desk..."machine broke" Techncians will understand that!!!

So does it see the drive at all? does it say use the whole drive? Does it give you how much space is available? Does it say theres a drive there? what options do you have available? what install are you going through, server install, desktop install, text mode, graphics mode, through a live disk? 

The main question is does it see the drive at all?

---

### Post by Ryadt on 2008-09-03
> **Bommetje said:**
> Hi,

I'm trying to make a dualboot on my system with Windows XP pro SP3 and Ubuntu 8.04.
I read different tutorials about how to do it but i'm kind of confused and hope you can help out.

According to several tutorials I read it says that during the part of the ubuntu installation where I should pick a partition I should pick Guided - resize partition, and it should recognise my WinXP partition, problem is I don't see this option at all.

So what i did is resize my partition in WinXP.
My WinXP partition was 200gb and I resized it too 160gb and left the 40gb unallocated.

Now when I get to the part of the Ubuntu installation where I should choose a disk, I pick manual but after that I'm at a loss at what to do.

Any help would be greatly appreciated.
Have a look here: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Bommetje on 2008-09-04
> **thesurgeon said:**
> 

So does it see the drive at all? does it say use the whole drive? Does it give you how much space is available? Does it say theres a drive there? what options do you have available? what install are you going through, server install, desktop install, text mode, graphics mode, through a live disk? 

The main question is does it see the drive at all?

It sees the disk just fine, and I can access the disk from ubuntu when it's running from the cd.
The drive is a Maxtor 6V200E0 SATA.

The options i have available during the install are:
Guided - use entire disk
Guided - use the largest continuous free space
Manual

I'm doing a desktop install through the live cd.
I also checked the live cd for errors in the boot menu and tried both the 32 bit and 64 bit version.

---

### Post by Sef on 2008-09-04
1) What is your largest contiguous free space?

2) System > Administration > Partition Editor

paste or type in this code:

```
sudo fdisk -l
``` Small L

That will show us how your hard drive is currently partitioned.  Paste the results here.

---

### Post by thesurgeon on 2008-09-04
Have you tried installing through a graphical mode and not through the live distro, it shouldnt make a difference but this is IT.

---

