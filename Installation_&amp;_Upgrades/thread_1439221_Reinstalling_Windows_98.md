---
title: "Reinstalling Windows 98"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by wuzeman on 2010-03-25
I have an old computer, it came with Windows 98, later I updated it with Windows XP. XP ran slowly because of it's outdated hardware. Around this time I already had a new computer. I decided to install Ubuntu on it to muck around with. However, Ubuntu also runs slowly and I have a dual-booting computer. However, when I try to get into the BIOS of the computer and run the 98 disk, I can hit every button and BIOS will not load. Question: How do I reinstall Windows if I can't access the BIOS?

---

### Post by Wiebelhaus on 2010-03-25
You can , you just have to figure it out. Google the model and "how to enter bios"

Cheers.

---

### Post by bpalone on 2010-03-25
Another option would be to remove the HD and put or hook it up to your other computer.  Then format it FAT 32 and install enough of DOS for it to boot up.  Then copy all of your 98 disk onto the HD.  Then reinstall it in the old computer, boot up and change into the directory with the 98 files and run setup.exe.

---

### Post by woodmaster on 2010-03-26
for old hardware like that, Ubuntu may not be the best choice.  Puppy Linux and DSL run gr8 on my old box w/ 128 RAM and a PII 300mHz;)

---

### Post by wuzeman on 2010-03-29
> **bpalone said:**
> Another option would be to remove the HD and put or hook it up to your other computer.  Then format it FAT 32 and install enough of DOS for it to boot up.  Then copy all of your 98 disk onto the HD.  Then reinstall it in the old computer, boot up and change into the directory with the 98 files and run setup.exe.
I've checked the hdd, it has pins. I'd need a special case, which I don't have. It's an old computer.

---

### Post by wuzeman on 2010-03-29
Alright so I checked all of the F keys, ESC, etc. I found one key that may work. When I hit F10 it goes into "Computer Setup" but do to the age of the computer, I don't know where to go from here. The full name is Computer Setup 686A1 11/11/98.

---

### Post by Serpher on 2010-03-29
Oh god not Windows 98. IMO try looking into Lubuntu. MUCH more lightweight than Ubuntu, and even then you can try DSM which can run on a god damn digital watch.

---

### Post by bpalone on 2010-03-30
Unless your new computer is ultra new, I am guessing that the CD/DVD is an IDE device.  If so, it uses the wide flat cable.  If that is the case, you should be able to hook the HD to that cable and accomplish the move.  Just be sure to copy everything from the CD to your HD in the newer machine first.  If the cable is old enough there will two connectors on it and one may be empty.  If that is the case, you may have to adjust the jumpers for master and slave, then use the empty connector and you would still have access to the CD.  I am assuming that the BIOS will detect the HD on the IDE channel.

Hope that helps you out a bit.

Just thought of this.  Even if your Cd is SATA, check the motherboard there may be an IDE connector there.  If that is the case just hook up an IDE cable and your set.

---

### Post by coffeecat on 2010-03-30
Why are you trying to get into the BIOS? Last time I installed Windows 98 it came on a bootable CD, iirc - it was about 11 years ago! :p. If you managed to install Ubuntu, you must have been able to boot up from the CD. Can you not boot up from the Windows CD?

If the Windows CD can't see the hard drive because of the Linux partitions, you need to run a live Linux CD (one of the lightweights suggested if Ubuntu won't run live), and reformat the whole drive as one FAT32 partition. (I presume it's smaller than 32GB - the W98 limit for FAT32.) Then the W98 installer should be OK.

---

### Post by cbecker78 on 2010-03-30
> **coffeecat said:**
> Why are you trying to get into the BIOS? Last time I installed Windows 98 it came on a bootable CD, iirc - it was about 11 years ago! :p. If you managed to install Ubuntu, you must have been able to boot up from the CD. Can you not boot up from the Windows CD?

If the Windows CD can't see the hard drive because of the Linux partitions, you need to run a live Linux CD (one of the lightweights suggested if Ubuntu won't run live), and reformat the whole drive as one FAT32 partition. (I presume it's smaller than 32GB - the W98 limit for FAT32.) Then the W98 installer should be OK.

Yah, If i remember my windows 98 installs correctly, that information is correct.  There shouldn't be a need to enter the BIOS other than getting it to boot from disk or cd.  If that is what you are trying to do... I might recomend "furiously" and repeatedly pushing the F1 -F12 keys during boot. (only one f key per boot).  I know it sounds dumb, but some of my older machines (way back when) never seemed to go to bios unless i kept on pushing it.  F2, F8, F4, and F12 are the ones that seem to come to mind as the ones that worked (depending on which pc i was at).  I'm pretty sure the stock bios on compacts circa Win98 was F8.

---

### Post by wuzeman on 2010-03-30
Is it possible to use GRUB's command line function to boot from the CD drive? I can boot from the CD, however I cannot get into BIOS to boot from the CD, if that makes sense.

---

### Post by bpalone on 2010-03-30
OK, do you have a 3.5 floppy in this machine?  If so, go to Boot Disk dot com and grab an image of the Win98 boot floppy.  There will probably be two, I would get the one without the ram disk as it seems to work better across many platforms.  It will have the driver for the CD, just watch what letter it gets assigned, as you will need it to start the install.

I think you will need the 3.5 floppy to install win98 if my memory is correct, I don't think 98 was self booting.  The version I have isn't and I am not an early adopter.  But some later ones may have been.  If it won't boot go get the image and make the floppy.  It will require windows r at least DOS.  I am not sure if it will unpack and burn under DOS alone.

Good luck.  It was late when I started answering you here was thinking you didn't have a working CD.  So, sorry for the hardware move suggestions.

---

### Post by RJARRRPCGP on 2010-03-30
> **coffeecat said:**
> (I presume it's smaller than 32GB - the W98 limit for FAT32.) Then the W98 installer should be OK.

FAT32 can work with up to 128 GB. 

With Windows 98, pretty much the only thing you have to worry about, is, if you have a hard disk drive bigger than 128 GB, because of the no-48-bit-LBA issue.

---

### Post by coffeecat on 2010-03-31
> **RJARRRPCGP said:**
> FAT32 can work with up to 128 GB. 

With Windows 98, pretty much the only thing you have to worry about, is, if you have a hard disk drive bigger than 128 GB, because of the no-48-bit-LBA issue.

Yes, you're right. I misremembered. The 32GB was a limit imposed by Microsoft (but only for creating a FAT32 filesystem) in 2000/XP. Again, iirc. :?

---

