---
title: "Uninstall 7.04 then install 7.10"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by DeadToad on 2007-10-17
I have Ubuntu Feisty Fawn 7.04 on a separate hard drive on one computer.  How do I uninstall it completely from this hard drive, so I can do a complete installation of Gutsy Gibbon 7.10 on the same hard drive.
I do NOT want to upgrade 7.04 to 7.10.  I want to do a complete installation of 7.10.
Thank you for your help.
DeadToad

---

### Post by blakeg on 2007-10-17
DeadToad,

You don't have to uninstall 7.04. Just pop in the 7.10 disc and format your hard drive accordingly.

BlakeG

---

### Post by wpshooter on 2007-10-17
> **DeadToad said:**
> I have Ubuntu Feisty Fawn 7.04 on a separate hard drive on one computer.  How do I uninstall it completely from this hard drive, so I can do a complete installation of Gutsy Gibbon 7.10 on the same hard drive.
I do NOT want to upgrade 7.04 to 7.10.  I want to do a complete installation of 7.10.
Thank you for your help.
DeadToad

Dear DeadToad:

Assuming that you do not have anything else (O/Ss, programs, and/or data) that you need to keep, the way I would do it would be to WIPE the hard drive clean by using the killdisk program.

[www.killdisk.com](www.killdisk.com)

---

### Post by DeadToad on 2007-10-17
blakeg, thanks for that, i didn't know that.

wpshooter, thanks also.

before i checked your replies, i booted with a windows boot disk, used fdisk to delete all partitions on that disk, then reformatted the drive, then used "fdisk /mbr" to fix the bootup.
all is good now.
will use killdisk next time.
thanks for your help.
DeadToad (ribbit)

---

### Post by diction on 2007-10-18
> **blakeg said:**
> DeadToad,

You don't have to uninstall 7.04. Just pop in the 7.10 disc and format your hard drive accordingly.

BlakeG

So I can basically tell it to overwrite my current Ubuntu partitions?

---

### Post by Sef on 2007-10-18
> So I can basically tell it to overwrite my current Ubuntu partitions?

The only partition that needs to be reformatted is your root partition where Ubuntu resides.

---

### Post by diction on 2007-10-18
> **Sef said:**
> The only partition that needs to be reformatted is your root partition where Ubuntu resides.

I also wanted to resize my swap partition. For some reason, when I installed Feisty, it ended up with less than 500MB. I've never even used my swap partiton yet (2GB of ram), but in case I need it, 500MB wouldn't be too useful...

---

### Post by blakeg on 2007-10-19
I run a partitioning scheme like /=10gb, /usr=10gb, /usr/local=10gb, 5gb swap and the rest of my 300 gig drive goes to /home.

When I reinstall ubuntu, I format everything except /home.

Formatting those partitions effectively removes the prior ubuntu version and installs whatever new flavor/version I want on it.

BlakeG

---

