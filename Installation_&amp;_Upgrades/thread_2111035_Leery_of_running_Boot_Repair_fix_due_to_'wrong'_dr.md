---
title: "Leery of running Boot Repair fix due to 'wrong' drive detection"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by DennisEHam on 2013-01-31
[http://paste.ubuntu.com/1595217](http://paste.ubuntu.com/1595217)  for boot repair report ala Ubuntu 12.04 LTS. (now running Ubuntu on DVD)

Wife's CPU (yup, I'm not in trouble yet as she doesn't know) is Vista with 10 gigs of pictures on it, and I wanted to wean her off Vista.  Can't find the Vista Recovery Disc and came across boot repair.

The suggested repair (if I interpret the report correctly) would restore the MBR on drive sda, but notice that SDA is a 200-gig drive partitioned into four drives and really is our secondary drive.  SDB is actually the 80-gig Vista boot drive.  And this is first time I tried to partition about 8 gigs of SDB to dual-boot Vista and Ubuntu.  The error message on bootup is error:no such partition grub rescue>  (I really would like to be able to boot into Ubuntu on that 200-gig drive but that's an issue for another day after I do some exploring on how to handle that.)  When I installed the 200-gig drive, I did not install it so that it would boot off the 200-gig drive.

So, I want to restore the 80-gig boot area so that the 8-gig or so Ubuntu partition is removed (and not touch this drive again!).

Please notice that the last page of the report on the topic of recommended repair never mentions the actual boot drive, the 80-gig SDB.  PS--I didn't mean to disparage boot repair with the 'wrong' comment as it looks like a fantastic tool, especially with the information it gathers.

Dennis

---

### Post by Mark Phelps on 2013-02-01
An alternative to boot-repair, if you're willing to shell out a few dollars, is to go the link below, download the repair CD image you want, and burn it to CD:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

### Post by offgridguy on 2013-02-01
If you can boot into windows, I would recommend backing up all your data, especially 10 gigs worth of pics, before you do anything else.

---

### Post by darkod on 2013-02-01
You have only Vista on that computer, right?

Try this first from live mode in Gparted. Open /dev/sda and remove the boot flag from sda1.

Reboot without the ubuntu cd and see if it boots straight to vista.

Of course, in BIOS sda should be the first disk to boot.

---

### Post by darkod on 2013-02-01
> **offgridguy said:**
> If you can boot into windows, I would recommend backing up all your data, especially 10 gigs worth of pics, before you do anything else.

It's not that tragic, or dangerous. Simply he's booting from sdb which has a broken grub2 on the MBR. That's it. If you boot from sda it should help, but not sure if it will solve everything since sda1 also has windows boot files but not windows itself. Not sure where vista files are, since windows can combine them with another version. It looks like vista has its own files on sdb1, lets see.

---

### Post by offgridguy on 2013-02-01
> **darkod said:**
> It's not that tragic, or dangerous. Simply he's booting from sdb which has a broken grub2 on the MBR. That's it. If you boot from sda it should help, but not sure if it will solve everything since sda1 also has windows boot files but not windows itself. Not sure where vista files are, since windows can combine them with another version. It looks like vista has its own files on sdb1, lets see.Thanks darkod, I was thinking he 
has 2 windows OS, but I have very little experience in this area.

=================== os-prober:
/dev/sda1:Microsoft Windows XP Professional:Windows:chain
/dev/sdb1:Windows Vista (loader):Windows1:chain

---

### Post by DennisEHam on 2013-02-03
Thanks all, especially darkod.  Here is the latest update on my efforts ~
 
-- while waiting on an answer to my post, I decided to play with the 2nd drive, the one with 200 gigs on it.  I successfully installed 2 versions of Mint 13 & 14 so that two of the four partitions on the 200-gig drive have Mint on them.  darkod got it right in that Vista is on /dev/sdb for the 80-gig drive, and /dev/sda is the 200-gig drive that previously had drives C, D, E and F on it with equal sizes.
 
-- When I made the post, I could not find out how to get back into Vista because 80-gig drive /dev/sdb reported the error about not finding partition and then it said 'grub rescue'.
 
-- VOILA, some progress after installing Mint 13 and 14 on 200-gig /dev/sda.  When I rebooted and chose sdb from the bios boot order menu, I noticed an entry that said Windows Vista /dev/sdb.  I chose that and WOW, Vista came back.
 
-- I think darkod is correct because I suspect that this grub program is on the 200-gig sda BUT not on /dev/sdb (the 80-gig).  I'm not sure why my computer thinks that the the 200-gig drive is /dev/sda because this Vista machine came with the 80-gig drive and has always booted into it first.  I later added the 200-gig drive and thot I did the jumpers correctly so that the 80-gig would be the Primary drive (another issue, I guess).
 
-- So, (having backed up the 10 gigs worth of pictures), I'm at the point of tryinig to get the 80-gig drive to boot again from its boot loader instead of the boot loader that is on the 200-gig drive.  I have several other computers and have been doing a lot in the past few days.
 
-- so now that Vista isn't the only OS on this 2-drive system and I don't have the original Vista disks, how to I get the correct boot loader onto the 80-gig drive so my wife doesn't get the grub rescue error when she turns on the computer, sits back and waits for Vista to come back up.  And then <grin> I hear,  "What is the world happened to my computer?"
 
Dennis
 
dennis

---

### Post by darkod on 2013-02-03
If you want a generic MBR on /dev/sdb which does the same job as windows bootloader, it's better to do it with lilo from live mode so that there are no traces of lilo in ubuntu.

So, boot the computer with your ubuntu cd in live mode, and in terminal do:
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```

There will be a warning about lilo config, ignore it and go on, that's normal. That will write a generic MBR to /dev/sdb. You might wanna double check that the 80GB disk is still sdb so that you don't write it on the wrong one.

Ubuntu is usually very good with the order of the disks. If it says the 200GB is sda, that means somehow bios is detecting that disk as first, then the 80GB. This is not issue at all unless vista expect to be on the first disk which windows sometimes does.

Try the lilo MBR, set bios to boot from the 80GB disk, and see how it goes. If it complains, you might need to reconnect the disks on the board. If these are sata disks, they are detected in the order of the sata ports on the board, so you need the 80GB in a port with a lower number than the 200GB.
If they are IDE, double check jumper master/slave settings and also which disk is in the Primary and Secondary IDE port on the board.

A slave disk in the primary port will still be detected ahead of a master disk in the secondary port.

If you use Cable Select, make sure you have it right. That's why I always preferred jumpers on IDE disks, instead of cable select. You set it as master or slave and don't depend on which connector on the cable you plug into it.

---

### Post by Mark Phelps on 2013-02-03
> **DennisEHam said:**
> -- so now that Vista isn't the only OS on this 2-drive system and I don't have the original Vista disks, how to I get the correct boot loader onto the 80-gig drive so my wife doesn't get the grub rescue error when she turns on the computer, sits back and waits for Vista to come back up.  And then <grin> I hear,  "What is the world happened to my computer?"
 
Dennis
 
dennis
I already answered this question for you -- see my earlier post #2.

---

