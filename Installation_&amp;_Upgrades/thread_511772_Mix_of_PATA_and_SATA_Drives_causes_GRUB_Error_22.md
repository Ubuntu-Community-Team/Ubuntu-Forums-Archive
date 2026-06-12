---
title: "Mix of PATA and SATA Drives causes GRUB Error 22?"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by gaalderman on 2007-07-28
Hello everyone!  I'm trying to set up an XP/Feisty dual boot on my new Asus P5B Deluxe/Intel Core 2 Duo E6600 box.  I've been running XP Pro on it since May but wanted to spin up Ubuntu on it this morning.  Here's the wrinkle.  I wanted Ubuntu on its own drive (guess I'm a little squeamish about resizing a perfectly healthy XP partition), so I pulled an PATA IDE hard drive out of an older computer and hooked it up, with the intention of giving it to Linux.  So now I have one SATA and one PATA.  

Now to set up Ubuntu.  The Ubuntu Live CD saw both disks, the PATA and the SATA, and was able to read the old PATA drive and set up up two Ubuntu partitions on it (one main partition to which I installed Linux and one swap partition).  The setup program ran through without a hitch, but on my first boot to Ubuntu, I got this:

GRUB loading Stage 1.5

GRUB loading, please wait...
Error 22

Which meant my MBR was hosed and neither XP nor Ubuntu would boot.*  I fixed that, so now XP and only XP is alive and kicking, but I want to dual boot.

Here's my question:  I've read in these forums that Ubuntu install has problems with machines that mix PATA and SATA drives.  Is that true?  Does anyone know where there's more information about that problem?  What's the workaround?  Do I simply have to suck it up and make room for an Ubuntu partition on my main SATA drive?  If so, can I use the PATA drive at all?

Thanks, folks!

______________________
*(NOTE TO NOOBS LIKE ME, IF THIS HAPPENS TO YOU,  IT'S AN EASY FIX.  Put in the XP install CD and boot to it.  When it prompts you, enter R to repair an installation. It will then give you a command prompt.  Type 

fixmbr

and when it asks you if you're sure, press Y.  Now you've got XP back.)

---

### Post by Pumalite on 2007-07-28
This is something to check:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#22)

I would say re-install Grub using these guidelines:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Or make yourself a Super Grub Disk and use that. In Asus mobos, go to BIOS and set IDE cong to Advanced Support for SATA+PATA.

---

### Post by MQMike on 2007-07-28
Sometimes the mixture of IDE and SATA works easily, by standard methods, sometimes it doesn’t.  I’m not sure I see any pattern.

Since you know how to fix the MBR, why not try re-installing GRUB to the MBR of the XP drive and set it up to boot both.  It’s worth a try, and seems to work often enough.  I'd bet it will go, but I'm biased in favor of GRUB.

First, you get into Ubuntu (Live CD), get a Terminal, get a GRUB prompt (type sudo grub and press Enter), and at that GRUB prompt, grub>, you re-install GRUB:

grub> root (hd1, 0)      #Ubuntu is in (hd1, 0), right – first partition, second hard drive?
grub> setup (hd0)     # That’s the MBR of the first drive, the XP drive
grub> quit
$ exit

Note:  
GRUB numbers hard drives and partitions starting from zero.  The first hard drive is hd0, and the notation (hd0) usually refers specifically to the MBR of hd0.
The sign # introduces a comment, and the comment is ignored by GRUB.

Next, you may have to get into Ubuntu and edit the boot menu (/boot/grub/menu.lst) with root privileges and File-Save, File-Exit when you are done editing. Edit menu.lst to include a valid entry for Windows.

title Windows XP
 rootnoverify (hd0, 0)
makeactive
chainloader +1

This usually does the trick for folks.

Re-boot to test it.

All details are in this How-To. The posts following the first post have other techniques, such as changing the default OS, etc.:

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by gaalderman on 2007-07-28
> **Pumalite said:**
>  In Asus mobos, go to BIOS and set IDE cong to Advanced Support for SATA+PATA.

:confused:In my BIOS settings I find that I can set the IDE configuration to Disabled, Compatible, or Enhanced (which is the current setting).  I don't see Advanced on that list.  Am I missing something?

Thanks

---

### Post by gaalderman on 2007-07-28
Thanks for the suggestions, guys.  

However, I still get no joy.  After trying MQMike's suggestions, I still can't boot, but now GRUB reports: 

GRUB loading Stage 1.5

GRUB loading, please wait...
Error 17

Error 17 is supposed to indicate an unrecognized filesystem.  This is confusing, because the Ubuntu partition is good ol' ext3.  

Any ideas?

---

### Post by Pumalite on 2007-07-28
> **gaalderman said:**
> :confused:In my BIOS settings I find that I can set the IDE configuration to Disabled, Compatible, or Enhanced (which is the current setting).  I don't see Advanced on that list.  Am I missing something?

Thanks

Enhanced will do. As for your error 17>Re-install Grub with Super Grub.

---

### Post by MQMike on 2007-07-28
When you hooked up the IDE drive, did you connect it to the * end * of the ribbon cable (the end closest to the middle connector)?  And then set it for Master and/or set BIOS for C/S (Cable Select)?

---

### Post by gaalderman on 2007-07-28
> **MQMike said:**
> When you hooked up the IDE drive, did you connect it to the * end * of the ribbon cable (the end closest to the middle connector)?  And then set it for Master and/or set BIOS for C/S (Cable Select)?

Yep, it's at the end of the cable and set for C/S.  Note that both Windows and the Ubuntu Live CD can see this drive, read/write to it and manipulate its partitions.  If there was a Master/Slave issue, the OSes wouldn't be able to see it at all.

Thanks,

---

### Post by rbmorse on 2007-07-28
Your motherboard uses the Intel P965 Express chipset with the ICH8 southbridge. PATA drives are controlled by an outboard jMicron 363 controller for which Linux support has been very, very problematic.  I had thought this had been fixed by now, but I guess not. 

Search this conference and the general conference using the term "ASUS P5B" for additional information and work arounds.

---

### Post by MQMike on 2007-07-28
Now that the jmicron controller was mentioned, I recall reading that, but have no clue what to do about it.

In the meantime, or just to get into this a little more, for your own edification . . .

If you just want to boot into Ubuntu, by any means, it would be interesting to see if you can.
Can you download and burn to CD the Super Grub Disk?

If so, you could see if it will boot your Ubuntu.

As a second experiment, see if you can do it manually:
Boot up SGD CD again.
When you see a menu saying press “c” key for a GRUB prompt, do so.
At the grub prompt, grub>, type
configfile (hd1, 0)/boot/grub/menu.lst

(which is where we think Ubuntu is, and we think the device naming is correct)

(And I think that’s it, you don’t need to type “boot” since you will immediately get a boot menu courtesy of Ubuntu.)

Super Grub Disk, new site:  [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Pumalite on 2007-07-28
[http://ubuntuforums.org/showthread.php?t=234706&highlight=jmicron](http://ubuntuforums.org/showthread.php?t=234706&highlight=jmicron)

---

### Post by kyphi on 2007-07-28
As MQMike has already pointed out, SATA and PATA hard drives do not mix if you want to dual boot .  Each runs through a different controller on the motherboard.

In fact, until the release of Feisty, PATA optical drives were not recognised by earlier versions of Ubuntu if you were using the P965 chipset, nor was the onboard ethernet connection.  Yes, they worked in XP but not in both operating systems.  The solution was simple: scrap all IDE drives and install an ethernet card.

Bottom line: use a second SATA hard drive for Ubuntu.

---

### Post by MQMike on 2007-07-28
kyphi:     "Bottom line: use a second SATA hard drive for Ubuntu."

I like that recommendation!  :)
That's the setup I have, two SATAs, and most tasks with GRUB are effortless following a few basic principles and commands.

---

### Post by kyphi on 2007-07-28
> That's the setup I have, two SATAs, and most tasks with GRUB are effortless following a few basic principles and commands.

Same here, MQMike, having the two SATA hard drives makes it all a piece of cake.

Computer equipment dates very rapidly and I do believe that it is inadvisable to take old and near obsolete pieces from an old computer and to install them into new machines.

---

### Post by gaalderman on 2007-07-29
Well, I DL'ed and burned the SGD (which is a very nice tool, I'm glad to have that, so one good thing has come out of this), and tried all of the boot methods you guys recommended.  I just get Error 17 no matter what I try.

But the rest of the discussion (and information in other discussions on this forum)  seems to be pretty clear in its implications:  Linux doesn't like this mobo's PATA controller chip, so I should go pure SATA if I want to dual boot.  Ain't nothin' perfect, I guess.  I just can't figure out why the Live CD saw the PATA drive at all if Linux doesn't like that PATA controller.  :confused:

OK, I'm off to buy another SATA drive.   Thanks for the help!

---

### Post by MQMike on 2007-07-29
Well, it's Sunday here in USA, so if that's where you are, at least there might be some good sales at Big Box stores.  You don't need an overkill.  Basic Linux install, 10GB the usual recommendation (3 GB for the bare root files).  Of course, add special apps, data, photos, whatever; but 80 GB would last most folks forever.  Good luck.  Let us know how this goes.

---

### Post by rbmorse on 2007-07-29
> **gaalderman said:**
> Well, I DL'ed and burned the SGD (which is a very nice tool, I'm glad to have that, so one good thing has come out of this), and tried all of the boot methods you guys recommended.  I just get Error 17 no matter what I try.

But the rest of the discussion (and information in other discussions on this forum)  seems to be pretty clear in its implications:  Linux doesn't like this mobo's PATA controller chip, so I should go pure SATA if I want to dual boot.  Ain't nothin' perfect, I guess.  I just can't figure out why the Live CD saw the PATA drive at all if Linux doesn't like that PATA controller.  :confused:

OK, I'm off to buy another SATA drive.   Thanks for the help!

The live CD can see the PATA drive because it gets disk services via the system BIOS..  The Linux kernel does not.

---

