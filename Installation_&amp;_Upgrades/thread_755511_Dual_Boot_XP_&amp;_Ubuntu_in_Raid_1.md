---
title: "Dual Boot XP &amp; Ubuntu in Raid 1?"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by ACMarina on 2008-04-14
I've done a pretty big search and have found a lot of information, but nothing quite along the situation I'm working with right now.

I've got a college student who has a PC, two 750 GB hard drives set in a Raid 1 Mirrored configuration.  "C Drive" is 250 Gig, contains Windows XP and some programs - "D Drive" is the media partition.

Well, Student wants to shrink "C Drive" and install Ubuntu.  

The only holdups from a complete migration - 

1. Homework is done in Microsoft Office 2007
2. Student watches Netflix "Watch Now" videos on occasion.

Now, we can easily shrink the "C Drive" partition to make a new one for Ubuntu.  The Raid 1 is the biggest hangup, though.  Student has a large collection of MP3s and Video on the "D Drive", and wants to have everything mirrored in the event of a drive failure.  If this were just a single drive, it would be no problem - but what about the fact that it's a Raid 1 setup??  

The motherboard is an Asus A8N-SLI-P, which seems to do software RAID.  Will having two different operating systems foul this up??  Will Ubuntu handle it the same way that Windows does, or is this a nightmare in the making??

---

### Post by ACMarina on 2008-04-15
Wow, guys - not a clue??  Am I gonna have to backup and guinea pig this one myself??

---

### Post by srossnz on 2008-04-15
> **ACMarina said:**
> Wow, guys - not a clue??  Am I gonna have to backup and guinea pig this one myself??

I'm in the same boat, seems to be a bit of a ghost town around here.  I tried booting to ubuntu, got to the setup screen but then it black screens on install.  After that my raid1 array breaks and both disks get listed in red.  I have to go into raid bios and set both disks as non raid, then boot back into XP and run intel matrix storage manager to rebuild the raid1.  I've done this 4 times already.  I guess switching to Ubuntu wasn't meant to be :(

If you get anywhere please Pm me and I'll do the same

---

### Post by dstew on 2008-04-15
If the disks are set up as a "FakeRaid", which is a type of hardware-assisted software RAID, then you can install Ubuntu onto it. It is a bit of a challenge. See the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto"). If it is a pure software RAID-1, then Ubuntu can be installed, and grub can dual boot it. See if you can detect the software RAID using mdadm from a Live CD boot first.

---

### Post by ACMarina on 2008-04-15
mdadm, okay - I'll check that out.

In the meantime, I'm wondering if it wouldn't be better to install a second drive to test this out.  If I install Ubuntu on there, it would humm along as its happy self, right??  

Now, here's the big question with this idea..

Let's say that the user downloads a file and saves it to the raid media drive.  It sounds like (from dstew's description) that it would mirror that with no trouble, right??

If both drives show up seperately, then what happens??  You save to one, and the next time you boot to windows it mirrors to both??  That's where I'm confused..

---

### Post by dstew on 2008-04-15
I believe that mother board uses the "FakeRaid" style of RAID, from looking at its specs. It is the NVidia type of RAID, that is enabled and configured in the BIOS. Therefore, you need to look at the FakeRaidHowTo for instructions, if you want to install Ubuntu on the RAID.

You can also install Ubuntu onto its own disk. However, to manage the RAID, you would have to make Ubuntu aware of it. I believe the Ubuntu **dmraid **program is the correct one to use with FakeRaid. I do not know if you install Ubuntu on its own disk if it will correctly recognize and be able to access the RAID without some help, but it might. Once the RAID has been recognized by Ubuntu, saving a file to the RAID is just like saving a file to any disk. Ubuntu treats the RAID as a single device.

The problem with installing Ubuntu on a separate disk is dual-booting. An easy way is to install the grub boot loader onto the Ubuntu disk MBR only, and pick to boot Windows on the RAID or Ubuntu on the separate disk using the BIOS. Trying to get grub to boot the RAID is difficult, I think. Look at the FakeRaidHowTo. Unfortunately, I have hands-on experience with software RAID only, but maybe someone else with FakeRaid experience can post to the forum.

---

