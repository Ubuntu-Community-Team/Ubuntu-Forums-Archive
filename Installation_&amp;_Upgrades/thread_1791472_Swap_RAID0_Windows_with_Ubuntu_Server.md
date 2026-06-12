---
title: "Swap RAID0 Windows with Ubuntu Server"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by thunderloki on 2011-06-26
Hey all -- please direct my attention to where it might be better suited if this question seems a bit off-topic.

Disclaimers aside, I have no idea how to go about this.  I have two questions:

1. What's a good way to back up my Windows 7 installation from my RAID0, replace it with my Ubuntu Server installation on my other drive, and then put the Win7 boot onto the non-RAID drive?  (and is there a way to do this without a 4th drive as temporary storage?)

2. I looked around a ton, but is the Asus P6-T motherboard hardware or software?  If it's software, is there even any benefit to using it?  And is it compatible with Ubuntu 11 x64?  ... Yeah, I know, that was like 3 questions in one.

Love to hear back from you guys on this one!  If anyone has any idea where I might find some of this info, if it's not available here, let me know.  Thanks. :mrgreen:

Bodie

---

### Post by thunderloki on 2011-06-27
(bump?)

---

### Post by YesWeCan on 2011-06-27
> **thunderloki said:**
> 1. What's a good way to back up my Windows 7 installation from my RAID0, replace it with my Ubuntu Server installation on my other drive, and then put the Win7 boot onto the non-RAID drive?  (and is there a way to do this without a 4th drive as temporary storage?)
Are you talking about swapping places between W7 on RAID0 and Ubuntu on non-RAID? I don't know how you do this with Windows. Have you considered a Windows forum like: [http://www.sevenforums.com/](http://www.sevenforums.com/)

It may be you can mount the Windows RAID using Ubuntu and then clone the Windows partitions on to a single disk using dd or similar. I have no experience of cloning a Windows RAID so I cannot advise.

As for Ubuntu that is no problem BUT you may be better off using linux RAID rather than FakeRAID (see: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)).

> 2. I looked around a ton, but is the Asus P6-T motherboard hardware or software?  If it's software, is there even any benefit to using it?  And is it compatible with Ubuntu 11 x64?  ... Yeah, I know, that was like 3 questions in one.It is software. The mobos, with the exception of some server mobos,  just provide some minor hardware support to enable Windows to do software RAID. Linux RAID does not require this and is considered better (around here at least).

---

### Post by psusi on 2011-06-27
Backup both systems, and restore them on the other drive.  You do have a regular backup procedure don't you?  If not, you need to get one or sooner or later you will loose your data.

---

### Post by thunderloki on 2011-07-09
(After some mucking about)

I've decided to use a Knoppix LiveUSB to clone my Windows 7 RAID 0 setup onto my single, non-raid 1TB hard drive.  The non-raid drive is of course larger.  I was actually wondering what method I should use for this.

I've tried GParted and it consistently gives me an error:

ntfsresize v2.0.0 ... ERROR(2): Failed to check '/dev/mapper/isw_cfjgibdeec_Velocityp1' mount state: No such file or directory
Probably /etc/mtab is missing.  It's too risky to continue.  You might try an another *[sic]* Linux distro.

My RAID 0 is called Velocity.  ls /dev/mapper/ gives:
control  /dev/mapper/isw_cfjgibdeec_Velocity  /dev/mapper/isw_cfjgibdeec_Velocity1

So my question is -- how the heck do I clone my RAID array!?  Maybe I should just use dd?  I'm not an expert but I'm not a complete noob either...

---

### Post by thunderloki on 2011-07-09
After much lurking, I have decided that a dd if=/dev/dm-0 of=/dev/sda will be for great justice.  Let's see how this goes.  Basically an identical case to this guy: 

[http://hardforum.com/archive/index.php/t-1299565.html](http://hardforum.com/archive/index.php/t-1299565.html)

Hopefully if none of you chumps have the force of will to wrestle with this beast, some noobs in my situation will eventually stumble upon this (perhaps fatally flawed) method for cloning a RAID0 Windows 7 installation to a new, EMPTY hard drive.  Obviously if you were to do this to a non-empty drive, it would suck.  Etc.

---

### Post by psusi on 2011-07-10
Apparently knopix is buggy.  Try gparted on the Ubuntu livecd.

---

### Post by thunderloki on 2011-07-11
Well, looks like all went well.  Hope this info helps someone in the future -- you CAN clone a RAID 0 onto a non-RAID drive using dd with if=/dev/dm-x where x is your particular managed device.

---

