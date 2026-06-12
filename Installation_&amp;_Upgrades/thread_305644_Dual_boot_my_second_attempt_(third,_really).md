---
title: "Dual boot: my second attempt (third, really)"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by igeterrors on 2006-11-23
My first attempt was actually pretty smooth -- installing Ubuntu Dapper on my laptop as a dual boot with Windows XP couple of months ago.  First time ever using Linux and I'm quickly sort of addicted.  So I make my second attempt, this time on my desktop PC, which is notable for its 256M of RAM (vs 512 on the laptop.)  To complicate matters, I installed a new 300GB hard disk on the desktop, copied the old XP partition to it (hda1, I suppose) and Windows booted up fine.  No LBA problem recognizing the extra large disk -- it sees everything.  So far, so good.  

I then move onto GParted, where I create the Ext3 and swap partitions on the new drive.  Again, smooth. Installing from the live CD was a little slow (256 RAM) and there was some trouble with Grub -- where to install it and so forth.  It didn't even ask when I did the laptop -- it just worked.  THis time, though, it involved about 2 days spent with various boot disks, the grub super disk, etc., trying to reinstall Grub and the MBR to the hard drive just to be able to boot the machine up at all.  At which point I was wishing I had just left well enough alone.  But I at least got everything back to XP booting fine off the new 300 GB hard drive.  I know I got a couple of grub errors, one of them (grub error 18 maybe) saying something about how the cylinder exceeds the max allowed by bios. I took this to refer to the 48-bit addressing issue, but since I know the bios already recognized the large disk, this didn't make sense.   

I then thought, well, I'll try again, only this time set up a small /boot partition as well -- maybe that's the problem with grub, it doesn't like being installed on a 95GB partition; and while I'm at it maybe a separate /home parition as well.  Why not?  Plenty of disk space.  But since I can only have 4 primary paritions (one NTFS for XP, one FAT32 for sharing, one swap and one Ext3), that meant I had to create logical partitions within the primary Ext3.  Right?  So I did.  I made the mistake of setting the boot flag on the /boot partition which led to another go-round trying to restore the MBR and make the machine bootable again.  Why this isn't as easy as when I did it on my laptop I have no idea.  Is it because of the new hard drive? 

Anyway, now I'm ready to try again, but with Xubuntu instead.  The Ubuntu live CD just moves like molasses, and the alternate CD seemed to be corrupted or something and if I'm going to do another 1-hour download, it might as well be for something that will be a little lighter on the system anyway.

This time, before I do anything, I'm asking for advice first.  For instance, best way to partition, primary vs logical, does the root part need to be at the front of the free space (after the FAT32)?  How big should the /boot part be?  Where should I install grub?  Which part should have the bootable flag?  (the part with XP, I assume, based on my earlier mishaps).  I've read lots of posts -- it's the only way I could've made it this far.  But this time I could really use help.  I know I've only posted general specs and what not, so if I need to post specific code please let me know what commands I need to get the necessary info.  

Thanks for reading.  Really, any advice at all would be most apreciated.  Thanks.

---

### Post by hardyn on 2006-11-23
i have done a dual boot about a dozen times with no problem, but i did do a new install of windows each time.  it there any reason that you are using such an ackward installation of windows?

every time i have done it i have booted the XP CD, partitioned my XP stuff... left the remainder of the drive alone.  and continued to install windows.

then pop in the ubuntu disk and basicly take all the defaults.  having ubuntu installer take care of the divy for the remainder of the drive.

what ram does your machine take?  if anybody on this forum is like me, im sure they have some old computer stuff kicking, and wouldnt mind parting with.  I am on a minimalist campagn right now and have been getting rid of all my old stuff, if it takes anything like old skool PC100, im sure you could find some cheap.

---

### Post by igeterrors on 2006-11-23
> it there any reason that you are using such an ackward installation of windows?

Not sure if you meant 'awkward' or 'backward' ;) or even what you're referring to.  Do you mean, since I was installing a new hard drive anyway, why didn't I just do a new install of Windows on it first?  The thing is, I wanted to keep all the data, files, settings, etc. from the old hard drive, so I didn't want to do a new installation of Windows.  So while I gave Windows a generous 90GB partition and about the same for the shared FAT32 partition, I intended the remaining 90 or so GB to be used by Ubuntu.  As I say, I installed Ubuntu just fine on my laptop this way and did not have to touch the NTFS partition at all.  Let me know if I misunderstood your question.

> what ram does your machine take? ... if it takes anything like old skool PC100, im sure you could find some cheap.

Sadly, it takes 800MHz PC800 RDRAM...  The machine's about 6 years old, but I have  a feeling that 256MB was too little even when it was brand new!  :)

---

### Post by hardyn on 2006-11-23
I have never had luck trying to do a big block copy of windows like that, if it worked last time, it worked last time... 

RD's.... yeah... a new computer is cheaper than that stuff...

---

### Post by igeterrors on 2006-11-24
> I have never had luck trying to do a big block copy of windows like that

OK, good, now we're getting somewhere.  It seems like you're saying that what I did is something that can be referred to, in whole or in part, as 'a big block copy of Windows.'  And sorry for being so questiony, but getting answers is why I'm posting here, so:

1. what is a 'big block copy of Windows?'
2. why is the thing I did called that? 
3. why is doing that something where luck is likely to play a role?
4. what should I have done instead?
5. what should I do *this* time?

:p

---

### Post by hardyn on 2006-11-24
1, basicly what you did, coping one partition to another.
2, im using my own jargon.
3, luck, hey hasn't worked for me.
4, im not going to tell you what you should or shoudn't have done, i know what you have done should have worked just fine; it has worked for several friends of mine, and that is usually how "restore disks" work... I do understand what a pain a reinstall of windows can be, but i have always done the full reinstall method.  its usually a good excuse to get all new drivers etc. anyway.
5, seeing as your system is disabled anyway... back up your data, blow up the partitions, and start again installing off the CD... now is also a good time to get a SP2 disk if you don't have one... keep your serial number, just use modern media.  and see what happens.

create the windows patition(s) leaving what ever space you want to use for ubuntu un-allocated, install windows, and then install what ever version of ubuntu.

at least this way if you continue to have problems, you know that you have done a text book install and the problem is not in your install method.

---

