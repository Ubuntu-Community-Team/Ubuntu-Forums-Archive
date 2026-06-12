---
title: "Operating System Not Found"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by wekebu on 2006-12-01
Hi,
Here's what I did to get this message.  I wanted a fresh install of Ubuntu.  I successfully ran the command 'shread -vfz -n 7 /dev/hda'.  Then I started to boot to a Desktop install CD and as it was starting to install I remembered that I wanted the wireless adapter card installed during the new install.  ...so I pulled out the power cord during the beginning of the install...](*,)  I know, you don't have to tell me...

Now I get Operating System Not Found.  I've tried booting to a Desktop CD, an Alternate CD and a Windows XP (which was never installed on this old computer).  I never get past this error.

My BIOS does see the HD and I've verified that the boot order is to the CD first (even reversed order to HD first in desperation).

Any ideas?

---

### Post by kdawg on 2006-12-01
Strange.... are you absolutely sure that it doesnt even prompt you to boot off the cd?  Thats weird that it will give you an OS error before trying to boot from a cd.  Try a partitionmagic disk if you have one, or any other partitioning software and wipe your drive, or a hard drive utilities disk, or a live cd like knoppix or something then run fdisk and wipe your partitions.  Surely it must boot from some CD!

---

### Post by christhemonkey on 2006-12-01
Or if you have another pc, wack the hard drive in there and reformat it.

---

### Post by wekebu on 2006-12-01
Hi,
Thanks for the advise. I removed the hd and put it into my XP machine.  Went into Disk Management and partitioned and formated the hd.  It took several minutes, but did say 100% formatted and said it was "Healthy".  I removed it, put it back into the old computer and I get Operating System Not Found.  When I turn on the computer, it splashes a Gateway logo (BIOS) and right as that screen is ending, I hear the hard drive spin up and the error appears.  I can Control/Alt/Delete to get the machine to reboot, but it's the same error.  I'm stumped...

---

### Post by wekebu on 2006-12-02
Okay, perhaps I formatted it incorrectly.  Do I want FAT, FAT32, or NTFS?  I'm planning on using only Ubuntu on the hard drive.  The computer was originally built in March 1999, so the motherboard is pretty old, as is the HDD, etc.  I was advised to partition, but should I use Windows to do the partitioning or if I can ever get the CD to boot, partition during the install?

---

### Post by Sef on 2006-12-03
> Okay, perhaps I formatted it incorrectly. Do I want FAT, FAT32, or NTFS? I'm planning on using only Ubuntu on the hard drive.

Use ext3, which is the default file system.

> I was advised to partition, but should I use Windows to do the partitioning or if I can ever get the CD to boot, partition during the install?


Ubuntu has a partioner one it.  It can automatically partition your hard drive.   If you want to install a home partition, then you will need to manually set up the partitions.  Read [Psychocats Installing Ubuntu]("http://www.psychocats.net/ubuntu/installing") guide, if you are using the Live CD.   If you are using the alternate CD, then read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/").  Note: This latter one is about dual booting, so just ignore when it talks about Windows.  The rest can apply to either a single or dual boot.

---

### Post by wekebu on 2006-12-04
Oh!  I can't thank you enough for answering me.  I had given up.  I can't get Ubuntu to boot from the cd, so I can't use the programs you suggested.  Or is there a way from my XP machine to get ext3?  I've tried booting to several versions of Ubuntu, desktop and alternate cd's. I think, perhaps, something is wrong with the master boot record because an install was interrupted?  (I have a dim knowledge of what I'm talking about.)  I made a bootable floppy (windows) and when I boot that computer, BIOS sees the RAM, processer, lists the HD, the keyboard, mouse, but no CD, when I go into BIOS, BIOS lists the Hard drive as primary boot master, it lists the CD as the secondary boot master.  No slaves are listed. Sounds correct, right?  When it boots to a: ,  I go from a: to c: it see the hard drive in c.  When I try to find the CD, nothing. Shouldn't the cd be assigned a letter, or am I thinking in DOS?  Is there such a thing as a bootable cd/floppy for Ubuntu.  I've installed another cd drive, same results. If I change the boot order to cd first, I get "remove disk or other media" "press any key to start" and it's stuck there.

---

### Post by Sef on 2006-12-04
> I can't get Ubuntu to boot from the cd, so I can't use the programs you suggested

Can you get the Live CD to boot from another machine?

If yes, then likely your BIOS is not set to boot from the CD first.  Do you know how to get into your BIOS?  

If no, then likely a bad download, a bad CD, or a bad burn.

Did you md5sum the download?

> Or is there a way from my XP machine to get ext3?

Download [GParted]("http://gparted.sourceforge.net/livecd.php").  It is the partioner that Ubuntu uses.  You can make the partitions with that.

---

### Post by eriefisher on 2006-12-04
What are the specs on the box? Maybe someone else has a similar box. The cd needs to be first on the boot list to boot the disc.

---

### Post by Delta_Farce on 2006-12-04
It sounds like BIOS isn't picking your CD up properly. Go into the BIOS and disable the CD ROM (ie set the value of the secondary master chanel to 'NONE') and then reboot.

BIOS should only report the hard drive.

Now reboot and go back into BIOS and set the secondary master to Auto. Save the settings and reboot.

This should force the BIOS to rescan your IDE channels and (hopefully) find the CD ROM again. 

If that doesn't work, try setting the CD ROM to be the primary slave (physically change the channels). As a last resort you might also be able to flash the BIOS (perhaps it was damaged).

Cheers,

Mark

---

### Post by wekebu on 2006-12-08
Thanks for all the suggestions.  I can get the CD to boot on another system.  The boot order is CD first.  I tried changing the CD to NONE, and BIOS didn't see the CD.  BIOS did re-id the CD on reboot. It earlier id-ed the replacement CD-ROM, giving me it's correct name. I tried moving the CD to Primary Slave.  When I change the channels on a CD-ROM is it the jumpers?  If yes, I tried slave and I also tried cable select. I started reading up on how to flash a BIOS, help me on that please.  PhoenixBios 4.0 Release 6.0 (not a 6.0.x.anything).  Is there a crash course on flashing bios?

Tell me, if my master boot record was damaged, would the system still boot to the CD?  How can I tell if it's intact?

I haven't tried gparted yet.  I'm too leery of Linux/Ubuntu and myself right now to try to partition it on my XP machine.  The more I read on gparted, the more confused I got...  It was operator error that got me into this mess, I truly don't want to destroy the one machine that's working.  Is there a crash course on gparted?

I no longer get "Operating System Not Found"  The only error I receive now is "remove disk or other media" "press any key to start"

---

### Post by wekebu on 2006-12-24
Update:  As it turned out, the second cd-rom drive that I installed was bad also AND the hard drive was dying.  I installed a third cd-rom drive and was able to get past the no operating system found error.  Then the hdd started giving all kinds of errors.  I replaced that with the only spare drive I had lying around and it booted to the cd and tried to install.  It's a longer story, but that drive is one that I removed from my primary computer months ago.  It died during the install.  At this point my hubby brought home his old computer from work for me to play with!  I'm happily running on it now.  :-D 

Thank you for the advise.  By the way, gparted worked well on formatting that old hard drive.

---

