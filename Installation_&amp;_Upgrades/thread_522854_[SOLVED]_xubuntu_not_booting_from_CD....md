---
title: "[SOLVED] xubuntu not booting from CD..."
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by QuadraQ on 2007-08-11
Hi all,

I've seen similar posts before, but my question is a little different. I have an old HP system that I'd like to load xubuntu on. It has 128 MB of ram, and a 166 Mhz Pentium. I've entered the bios and set it to boot from the CD-ROM drive first, popped in the latest i386 xubuntu alternate CD I downloaded using bittorrent, and nothing seems to happen. I just get a blinking cursor in the upper left corner, and that's it.  Any ideas on what I could be doing wrong? Any suggestions? Thanks in advance.

---

### Post by merlinus on 2007-08-11
Did you do a checksum on the download?  Check cd for errors?  Burned at 4x or less as a disk image?

Can you try booting from it on another machine?

-merlin

---

### Post by QuadraQ on 2007-08-11
I have done an MD5 checksum and they match. I didn't burn at less than 4x, but on my main machine I can boot from the disk just fine.

---

### Post by merlinus on 2007-08-11
Did you burn the cd on this machine?  If not, that may be causing your problem.

Also, there may be a problem with the cd drive.  You might try cleaning the lens.

Even with video incompatibilities, you should at least get to the opening menu.

-merlin

---

### Post by QuadraQ on 2007-08-11
Well I know the CD-ROM drive is perfectly capable of reading the CD. If I boot into the Windows 98se that's currently installed on the hard drive, I can read the contents of the CD just fine.

What's interesting is that SOMETHING is happening on boot-up just not successfully. I tried putting in a blank CD-R disc and it just skipped over the CD-ROM drive in the boot sequence and booted from the hard drive. When I use the xubuntu CD it doesn't do this, it stops and gives me a blinking cursor. It's like it's attempting to boot from it but just never gets anywhere.

Since I know the CD can be read in the drive, is there a way to boot from a floppy, then activate the cd install?

---

### Post by 0graham0 on 2007-08-11
how long have you waited with the blinking cursor?

---

### Post by merlinus on 2007-08-11
So perhaps there is something wrong with the download and/or burn.

Can you try the cd on another computer?

-merlin

---

### Post by QuadraQ on 2007-08-14
> **merlinus said:**
> So perhaps there is something wrong with the download and/or burn.

Can you try the cd on another computer?

-merlin

Well as I said the CD boots fine on another system.

To address the other question, I have waited about 5 minutes to see if it was just slow, but nothing happened.

Here is a picture of the boot options screen in the bios:

[IMG]http://www.miscbackup.info/BootOptions.JPG[/IMG]

Is there anything in there that could be causing a problem? I tried changing the System Cache on an off as well as the Boot Speed, and neither made any difference.

The system I'm trying to install this on is an HP Pavilion 7170 with the memory maxed out to 128MB and a PCI network card installed.

---

### Post by QuadraQ on 2007-08-15
OK some more info...

I downloaded Damn Small Linux (DSL) since it has a floppy boot option. I couldn't boot from their live CD (same problem), but was able to boot from the floppy, and from their to use the CD to boot into a Live version of linux. So the CD-ROM drive works, it's just not bootable. So is there anyway I can use a boot floppy to get started, and from their start the xubuntu CD?

---

### Post by logos34 on 2007-08-15
> **QuadraQ said:**
> OK some more info...

I downloaded Damn Small Linux (DSL) since it has a floppy boot option. I couldn't boot from their live CD (same problem), but was able to boot from the floppy, and from their to use the CD to boot into a Live version of linux.** So the CD-ROM drive works, it's just not bootable. So is there anyway I can use a boot floppy to get started, and from their start the xubuntu CD**?

You want Smart Boot Manager.

You need to copy the 'sbm.bin' image (~1.4 MB) on your (X)ubuntu install CD to a floppy.

Use rawwrite (on windows):

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

Or 

'dd' (linux)

sudo umount /media/floppy0
sudo mkfs.msdos /dev/fd0
cd /media/cdrom0/install
sudo dd if=sbm.bin of=/dev/fd0

---

### Post by QuadraQ on 2007-08-16
Thank you very much for the correct info. I discovered this on my own last night, and it does indeed solve the trouble. I was able to use the 7.04 alternate install CD with the bootfloppy to install xubuntu. It's still not working, but that's a problem for another thread...

---

