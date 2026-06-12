---
title: "Question about installing on a drive with files on it already"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by mcar2185 on 2007-07-18
Alright, here's the scenario:

I have an HP Pavillion Desktop PC with the following specs:
512MB RAM
Pentium III Processor
13.6GB HDD (with XP Pro installed--drive C) and a 90GB HDD (with just random programs and files--drive D)
ATI Radeon 7200 Graphics card
CD-RW drive
Ethernet card

What I'd like to do is install Ubuntu Desktop on the 90GB HDD. How can I do this without overwriting the current files on there? And could I then boot between XP and Ubuntu despite the fact they are on two different HDDs? Thanks and I apologize if this question has been dealt with before.

---

### Post by steevols on 2007-07-18
It's very easy, thanks to the Ubuntu Installer GUI. All you have to do is select the 90GB in the installer's partition editor, and squish the existing (NTFS? FAT32?) partition down at least 3 or 4 GB's... Then, it's pretty straight forward. Be sure to leave about twice your amount of RAM for the swap file, which also happens to be a partition.

---

### Post by mcar2185 on 2007-07-18
I've been trying to install the latest version of Ubuntu and it freezes each time (black screen). Any idea why it's doing this?

---

### Post by merlinus on 2007-07-18
ATI video card.  Try the text-based Alternate Desktop install cd.

Once it is up-and-running, you can do a search and install the appropriate drivers.

-merlin

---

### Post by mcar2185 on 2007-07-18
Do I have to disable the video card at all before using the alternate install? Also, is it more difficult to do the text based alternate install? Thanks!

---

### Post by merlinus on 2007-07-18
No, and no.

Post here if you run into difficulties.

Good luck!

-merlin

---

### Post by mcar2185 on 2007-07-18
OK, I have a question about partitioning the disk. I want to run Ubuntu from Drive D (not drive C, the primary drive with XP installed). Which of the partitioning options do I select to do this?

1.Guided - resize
2.Guided - use entire disk
3.Guided - use entire disk and set up LVM
4.Manual

---

### Post by merlinus on 2007-07-18
Manual, unless you want to re-size your windows partition (c) and install in the free space.

If you desire the re-size option, then beforehand delete all temporary files and anything else no longer needed, and defrag several times.  

-merlin

---

### Post by mcar2185 on 2007-07-18
Thanks. Got another question:

I go into manual and see the two options:
SCSI2(0,1,0) - 100.0GB ATA Maxtor
#1 primary 100.0GB K ntfs /media/sdb1

Which do I select to partition if I want to keep the files on the drive intact?

---

### Post by merlinus on 2007-07-18
Which one has the files?  Use the other one.

-merlin

---

### Post by mcar2185 on 2007-07-19
Well, I ended up partitioning it. It isn't a huge deal if I lose the files on the drive (they're all on my laptop now) but I think I did it right. Since the drive is about 92GB after the format I did when I installed the drive, I ended up leaving about 10GB free for Ubuntu, while the other partition is roughly 82GB. It's still installing, so I'll let you know if I have problems. Thanks!

---

### Post by mcar2185 on 2007-07-19
OK, it rebooted after finishing. It tries to load Ubuntu but after the initial screen, it just goes black. Help?

---

### Post by merlinus on 2007-07-19
Press "Esc" when prompted to display the grub boot menu, boot into recovery mode, login...then enter:

(or Ctrl-Alt-F1 to get to prompt)

sudo dpkg-reconfigure xserver-xorg

You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:

startx

or reboot...

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

-merlin

---

### Post by mcar2185 on 2007-07-19
Thanks again. I did that and now get this error:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? What do I do next?

---

### Post by merlinus on 2007-07-19
If you selected vesa as your video driver, make sure you selected the right bus id.  That may be causing the problem.

-merlin

---

