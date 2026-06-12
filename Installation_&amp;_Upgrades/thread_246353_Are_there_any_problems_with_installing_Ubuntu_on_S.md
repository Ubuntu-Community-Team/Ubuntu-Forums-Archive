---
title: "Are there any problems with installing Ubuntu on SATA disk?"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by g0nzo on 2006-08-29
Hi!

I decided to install Ubuntu, but after looking through the forum I noticed that some people have problems with installing Ubuntu on the SATA disk where they already have Win XP installed.

In my case it's rather not an option to reinstall the whole Win XP. So are there any problems with installing latest version of Ubuntu (or rather booting to Win AFTER installing Ubuntu) on SATA disk where I already have Win XP (NTFS)?

Thanks in advance

---

### Post by ciscosurfer on 2006-08-29
I haven't seen that many people have this problem (although I'm sure some discrepencies exist).  Backup your important XP stuff (just in case a dual-boot install of Ubuntu/XP fails and corrupts the disk), then try installing it...

I run XP on my first drive, and Ubuntu on a second drive.  This is probably the best way to set things up so there is absolutely no conflicts between OS' on the same drive.  These days, drives are cheap.  Buy an extra drive, install it, and then have fun!

And keep in mind, that XP likes to be installed first (issues with MBR, etc.) and then you should install Ubuntu over it/along side it.

---

### Post by zxee on 2006-08-29
From what I've seen here and read about at the ubuntu official install site
It's always good to check the hardware specs there [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
There can be problems with ide/sata combinations so if you do get a extra drive perhaps it should be another sata.

---

### Post by ciscosurfer on 2006-08-29
@zxee
I run XP on an IDE drive; Ubuntu on an SATA drive.  No problems here. ;)

---

### Post by zxee on 2006-08-29
> **ciscosurfer said:**
> @zxee
I run XP on an IDE drive; Ubuntu on an SATA drive.  No problems here. ;)
Yup that will work. But if the sata drive is the 1st boot drive, as I think is the case with the OP, then grub/ubuntu will see any added ide drive as the 1st boot drive even if it isn't.

---

### Post by ciscosurfer on 2006-08-29
That's interesting.  Are these the issues some people are having when installing XP to an SATA drive and Ubuntu to an IDE?

---

### Post by caiman64 on 2006-08-29
I used to have 2 healthy SATA disks on my system. I installed UBUNTU and It killed my WinXP... since then I am not being able not even to reinstall XP again,,, looks like UBUNTU does something to the disks so that XP can not be installed again... I seriously advice against installing UBUNTU in a productive machine with Windows XP... Try it on another machine... The community has not been helpfull on this issue... WATCH OUT

Regards
Carlos
](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by ciscosurfer on 2006-08-30
caiman64,
As some have noted, there may be some issues/bugs with installing Ubuntu and XP as a dual-boot scenario on one SATA drive.  The community is quite robust and can help you if you have problems.  Perhaps you installed Ubuntu over your XP install or perhaps you deleted the info on your MBR...other scenarios are quite possible as well.  I would suggest starting a new thread in which you describe the problems you have or are having.  A good rule-of-thumb, is to always backup your data before doing any major improvements/changes to your system (i.e., installing a new OS).

---

### Post by g0nzo on 2006-08-30
> As some have noted, there may be some issues/bugs with installing Ubuntu and XP as a dual-boot scenario on one SATA drive.

That's exactly my case :)

But even if Ubuntu (or rather grub) messes something with booting, shouldn't "fdisk /mbr" fix it (at least I should still be able to boot to Windows)?

---

### Post by gng4life on 2006-08-30
Hello,

I have two installations of Ubuntu/XP on two different PCs, both with a mix of SATA/PATA drives.  Both PCs have both XP/Ubuntu on the same disk, just different partitions.  I used the EXT3 for Ubuntu and NTFS for XP.  Unless GRUB corrupts your MBR, you shouldn't have any problems with it.  I agree with the earlier post about installing XP first, had many problems with another build when I didn't have XP loaded first.  I also have a laptop with XP/Ubuntu on it, same drive, two partitions.  So far, I haven't had any problems with any of them (XP/Ubuntu).  Of course, back-ups are ALWAYS the way to go before setting forth on a new journey...Take care

---

### Post by frodon on 2006-08-30
I installed ubuntu after XP on my 300Go SATA drive which contain both OS now without any problems.
All worked out of the box.

Some users which don't have motherboard embedded SATA chipset may have some problems because some SATA cards are not well supported by ubuntu.

I confirm as well that the easiest way to install both OS is to install windows first.

@Caiman64, almost all problems have solutions, if you wish some help just open a thread with clear details on what happened and make you say ubuntu killed my XP partition.  AFAIK except user mistakes during the partition step this almost never happen.

---

### Post by g0nzo on 2006-08-30
Thanks, I'll give it a try.

Just few questions:

- should I prepare new partition in windows and let ubuntu just change filesystem to ext3 or it's better to let ubuntu do everything for me?

- can ubuntu damage something else than mbr? if not, there's no need to backup anything, as i could plug my disk into another computer and get all data back. Or...

- if ubuntu messes up mbr, will booting with windows boot disk and "fdisk /mbr" help with it? It should overwrite anything ubuntu writes to mbr, so i assume it should work. Just trying to make sure of possible fixes before starting installation :)

---

### Post by frodon on 2006-08-30
> **g0nzo said:**
> Thanks, I'll give it a try.

Just few questions:

- should I prepare new partition in windows or it's better to let ubuntu do it for me?It's not needed, the dapper desktop CD use a graphical partition tools which looks like partition magic so it's really easy to do. But if it provides you peace of mind to do it under windows because you're used to its partition tool then go for it.> **g0nzo said:**
> - can ubuntu mess something else than mbr? if not, there's no need to backup anything, as i could plug my disk into another computer and get all data back. Or...In theory no, but making a backup or better a ghost of your windows partition is never a waste of time, so if it's not painful for you i would advice you to make one.> **g0nzo said:**
> - if ubuntu messes up mbr will booting with windows boot disk and "fdisk /mbr" help with it? It should overwrite anything ubuntu writes to mbr, so i assume it should work. Just trying to make sure of possible fixes before starting installation :)You can fix MBR with both ubuntu and windows install disk easily.

---

### Post by martinrandau on 2006-08-30
I seem to have problem with installing on a SATA hd (Toshiba 120Gb). 

The problem is partitioning. I have windows on sda1 and I want to resize it to fit ubuntu. I have tried gparted both with the boot flag set and unset (through fdisk). The error message I get is not informative at all, saying only that this failure might affect the other operations.

Running gparted outise of the setup shows that the problem is the resizing part.

---

### Post by g0nzo on 2006-08-31
Thanks for all replies!

I've managed to install Ubuntu without any problems :)

---

### Post by martinrandau on 2006-08-31
Not even Partition Magic can resize my ntfs partition on the 120Gb Toshiba SATA hd! What the hell is going on here?

---

### Post by randell6564 on 2006-08-31
> **g0nzo said:**
> Hi!

I decided to install Ubuntu, but after looking through the forum I noticed that some people have problems with installing Ubuntu on the SATA disk where they already have Win XP installed.

In my case it's rather not an option to reinstall the whole Win XP. So are there any problems with installing latest version of Ubuntu (or rather booting to Win AFTER installing Ubuntu) on SATA disk where I already have Win XP (NTFS)?

Thanks in advance

Hi! this may answer your concerns.  
[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

---

### Post by mxreader on 2006-08-31
I got problems with my setup.  Fortunately XP is still working.

XP is on the IDE first drive, I got a second SATA drive using the Promise PDC203476 controller where Ubuntu is currently in coma.

2 versions of Ubuntu back I got alternate booting working. Installed the Ubuntu on the SATA as the case now except that I completely disconnected the IDE when installing Ubuntu on the SATA, this means I had to go to BIOS and swap first boot drive to choose the OS.  It worked fine since I dont change that frequently, getting used to Ubuntu and running it most time.

An update became available. After updating Ubuntu to the next version, the GUI broke (X window?) so I had to forget Ubuntu for a while hoping the next version would fix things.  The next version came which is Dapper... waited until this week to attempt proper Dual booting or so I thought.  Ran the liveCD and let it install and selected the automatic partition of the whole SATA drive.   It was immediately disappointing when the wireless did not work, I tried the old solution of editing the interfaces file but that did not fix the problem with this new version.  Had to switch to XP to connect to the internet and read some info for that problem.  Decided to call it a night and shut down the PC.  Next boot up I selected Ubuntu from the Grub menu and that was when a second more serious problem came up... cant even boot Ubuntu!

IDE (XP) & SATA (Ubuntu) dual booting did not work for me.  The new version is becoming a big disappointment.

Randell, I keep going to that link you provided and even identified my HDD setup, but its all gibberish to me.  The workarounds at the top of the page of that link is far to dangerous to attempt, not to mention time consuming for a newbie.  Workaround 3 means I have to buy an extra ATA drive just so I can "migrate" it to the SATA.... and what does "migrate" entail? no those are not options I could consider.

---

### Post by linuxpenguin on 2006-08-31
I've got a laptop with 2 SATA drives, Ubuntu had no problem installing.

Strangely enough, WinXP simply **refuses** to install -- even though this laptop came with Media Center Edition preinstalled. . . I'm guessing it doesn't like installing to the secondary drive for some reason. . . I'm thinking I just might try ReactOS instead though.

---

