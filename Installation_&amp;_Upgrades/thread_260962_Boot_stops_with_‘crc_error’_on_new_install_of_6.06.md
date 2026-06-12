---
title: "Boot stops with ‘crc error’ on new install of 6.06.1"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by Locksmith on 2006-09-19
I would really appreciate any help and pointers that anyone can give me.  I have struggled under the burden of a bloated OS from Redmond for many years and have finally taken the plunge to break free and adopt Linux.

Sadly, although I can get the ‘live’ CD to run perfectly on my PC (from the CD drive), I cannot get it to run at all once installed to the hard drive.  I‘ve been trying for about 5 days.

Everything goes perfectly, until I reboot the PC and it tries to start up Ubuntu from the hard drive.  After working through a few steps, it just stops with “crc error, system halted” and will not respond to the keyboard.

I have tried…..
[LIST]
[*]Reformatting hard drive (include a full, low-level re-format, of all areas – boot sector, the lot - using the HDD maker’s utility)
[*]Running ‘Memtest’ for about 4 hours (all passes, no fails)
[*]Re-installing (at least 4 times)
[*]Installing using graphical mode (Ubuntu) and text mode (Kubuntu)
[*]Using the built-in CD verification routine to test the installation CDs (perfect on both CDs)
[*]Taking out one of the memory banks (in case the ‘256 + 128’ configuration was causing problems)
[/LIST]

None of these actions made any difference to the outcome.

The full message that I got back on the latest install attempt (Kubuntu) is as follows (all of the previous messages were pretty similar)…

[FONT="Courier New"]Booting ‘Ubuntu, kernel 2.6.15-26-386’
Root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
Kernel  /boot/vmlinuz – 2.6.15-26-386 root=/dev/hda1 ro quiet splash
[INDENT]Linux-bzImage, setup = 0x1c00, size = 0x1578d][/INDENT]
Initrd  /boot/initrd.img – 2.6.15-26-386
[INDENT]Linux – initrd @ 0x1796a000,0x675b0c bytes][/INDENT]
Savedefault
Boot
Uncompressing Linux
[INDENT]crc error[/INDENT]
[INDENT]system halted[/FONT][/INDENT]

My system details are (it was a good spec in 2001 ;) )
[LIST]
[*]Motherboard = QDI KinetiZ
[*]CPU = AMD Duron 750 MHz
[*]Memory = 384 MB (128 + 256)
[*]HDD = Fujitsu IDE 15 GB (connected as Primary IDE Master)
[*]CD RW (connected as Secondary IDE Master)
[*]Graphics = Voodoo 3
[*]Sound = Soundblaster SB16
[*]Network = Netgear FA311 (not connected to a network)
[*]No USB devices (or printer, etc) connected
[/LIST]
The system was previously running Windows 98SE, but has been thoroughly expunged by re-formatting of HDD (including low level format using Fujitsu’s utility).

I’m really keen to get Ubuntu working and somewhat embarrassed that I can’t fix it (especially having read how easy Ubuntu is to install).  All assistance greatly appreciated.  Thanks in advance.

---

### Post by Peturrr on 2006-09-20
Could you try to hit the ESC key when you see GRUB saying, booting in 2 seconds. press ESC for options or something like that.
It appears right after the BIOS. 

You'll get a menu with several kernels and then select the [recovery mode] kernel. It will give you more output so we can see what's going wrong. Please write down the lines before your error and post them here.

---

### Post by Locksmith on 2006-09-20
Hi Peturrr.  Thanks for response.  I have re-tried your suggestion -  selecting [recovery mode] -  and the error message is exactly the same as when booting in 'normal' mode (see above).  I apologise, I should have mentioned in my original post that I'd already treid this upon each failure.  Since you suggested it, I have tried again.  Same results.  Is there any other route into a diagnostic panel (e.g., holding F1 during boot)?

---

### Post by wpshooter on 2006-09-20
3 things to try.

1) Although I don't think this is the problem, but humor me, and get a CD cleaning disk and clean your CD drive.

2) Go to the CD manufacturer's website and make sure that your CD drive's firmware is on the latest and greatest version.

3) Go to this website and download Killdisk program and WIPE your hard drive and afterwards try downloading, burning and installing from the ALTERNATE version of Ubuntu 6.06.1.  Make sure you run CD integrity test from initial boot screen menu first.

[http://www.killdisk.com/](http://www.killdisk.com/)

Good luck.

---

### Post by Locksmith on 2006-09-21
Hi.  Thanks for suggestions.  Can I ask a couple of questions about them ?  General stuff first...What you're suggesting seems to indicate that the fault may lie with the CD Drive.  Since the CDD is about 6 years old, well thrashed and not top quality to start with - what are your thoughts on total replacement (including recommendations for drives of adequately superlative quality to deal with Ubuntu installations) ?  Also, since every insatllation has apparently gone perfectly (until I try to boot from HDD) this begs the question - why on earth doesn't the Ubuntu installation package perform some kind of self test of the files written to the HDD, before saying "All OK - go ahead and re-boot" ?

Turning to specifics..
1. When you say 'Firmware', is this the same as a 'Driver' ?
3. When you recommend 'killdisk', no problem, but is this any better than Fujitsu's own erase package (writes 00 to every part of every sector) - I only ask, as I've already used the Fujitsu package. 

Cheers

---

### Post by wpshooter on 2006-09-21
First of all there is no assurance that the problem is the CD drive.  But as a first step I would check to see that the firmware is up-to-date.  And no, firmware is not the same as driver.  Most modern O/Ss have drivers to the CD drive built-in.  The firmware actually is installed to and resides on the CD drive.  It must be basically burned to the drive - you are probably going to have some type of windows O/S installed to possibly update the firmware (unless they have an firmware update that will function from a bootable floppy), and I don't know that the firmware updates can be done from a Linux O./S - I have never had occasion to try - and probably a mute point since you haven't been able to get a Linux/Ubuntu O/S to install yet.  The drives manufacturers website should tell you if your firmware is up-to-date.  Most systems will display the current firmware version installed to the CD drive on the initial system boot screen.

If you really wanted to replace the CD drive, my recommendation would be a **Plextor**, either a DVD-RW or a CD-RW or a combination of these two type, what ever might suit your needs.

As far as the killdisk program, my preference would be to use that as opposed to the one by Fujitsi because I am wondering if it is really getting rid of EVERYTHING including partitions, etc., that may be causing you an installation problem.

Did you try simply cleaning the CD drive ?

---

### Post by Locksmith on 2006-09-23
Well.  Tried almost everything suggested and still no good.  Here's what I did..
1. Cleaned the CD Drives (Burner on this PC and reader on the old hack - the one that's getting Linux).
2. Burned a new iso (Kubuntu - Alternate), using Nero 7, at only 16x and with all relaxations removed (as pure as you can get)
3. Did low level format if HDD with Killdisk.
4. On booting, got exactly same crc error as on previous 6 or 7 installs (and same whether using normal or recovery mode boot).

Unable to update Firmware of CDD (CyberDrive CW018D)  - found CyberDrive Firmware on their website, but this model is too old to be still supported.  Searched web, but nothing that looked useful.

So - what next ?  All I can thik of is lashing out some cash and getting a new CDD (Plextor PX230A looks reliable/good value).

Does anyone have any further thoughts ?  I'd really like to get some more diagnostics as Ubuntu boots, but can't fid a route to do this.  Hope that *using *Linux does not require same patience/tenacity as *installing *it ;-)

---

