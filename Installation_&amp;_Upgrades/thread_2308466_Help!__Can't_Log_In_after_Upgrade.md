---
title: "Help!  Can't Log In after Upgrade"
date: 2016-01-03
forum: Installation &amp; Upgrades
---

### Post by Angela_C.Murphy on 2016-01-03
I finally got around to upgrading my Ubuntu 12.04 LTS to Ubuntu 14.04 LTS last night.  Big problem resulted.  When I restarted and every time since then, I first see "error - file not found" three times, then the GRUB boot menu comes up.  When I select "Ubuntu" the log in screen comes up, but when I try to log in, whether as the root user, myself or my husband, I get a white box that gives me the choices "Cancel" or "Report this error" and then I am bounced right back to the log in screen.  I've tried to use the recovery options, but I don't really know how to do so effectively, except to use "fsck", and that doesn't tell me much.  I can use the GRUB menu to boot into windows and an old Xandros Linux, but not into Ubuntu 14.04.

 I have a Live DVD of Ubuntu 14.04.3, but I don't know if I really have to make another partition on the disk and install from scratch, giving up on the partition where I just upgraded.

I would be most grateful for any help.  I'm not an expert, just a run-of-the-mill user.

Angela C. Murphy

---

### Post by oldos2er on 2016-01-03
What are your hardware specs, particularly video card and drivers in use (if you know)? Were there any errors shown during the actual upgrade process?

---

### Post by Bashing-om on 2016-01-03
Angela_C.Murphy; Hello;

Interesting little situation you have developed .
What pops to mind for me is that in the 12.04 install you had a proprietary graphics driver in use .
Now maybe that hardware is no longer supported or the driver is broke in 14.04.

Let's isolate the problem to being in the X layer of the operating system.
If the system foundation is consistent, you can boot to terminal from grub.
From this terminal we can further investigate the cause of the issue.

Boot to the grub boot menu, here with the latest kernel selected, press the 'e' key for edit mode -> boot parameters screen;
In this screen arrow down to the line starting with linux and across to quiet splash, replace quiet splash with the term "text" - with out the quotes. press key combo ctl+x to continue the boot process to terminal (TTY1) .

Can you login here with the primary user name and your pass word - no response to the screen when pass word is entered - ?
Enter your password blindly and hit the enter key.

When you get to this point, we can have a looksee within the terminal to see what the situation is.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Angela_C.Murphy on 2016-01-04
Sorry, I thank both of you for trying to help, but my question became moot yesterday.  In trying to set up a partition to install Ubuntu 14.04.3 from the live DVD, I accidentally wiped the whole disk.  I then had to re-partition everything on that disk, and set up partitions for Ubuntu 14.04. Windows data, Ubuntu 12.04 and Ubuntu Swap.  I installed 14.04, from the live DVD, and I now am using 14.04 Firefox to write this.  I then restored my Windows data and 12.04 partitions from Backup images, using Acronis and Clonezilla respectively.

Let me explain my stuff a bit better.  I have a 10-year-old Dell Dimension 4700 desktop.  It has a pentium 4 processor, 4 Gb of memory and a fairly new Sapphire Radeon video card.  It has 2 Western Digital SATA hard disks - disk A, 160 Gb, running Windows 7 and Disk B, 325 Gb, which has a logical Windows data partition and 3 primary partititons,
Ubuntu 14.04 LTS, Swap, and Ubuntu 12.04 LTS.  There is also extra space.

Ubuntu 14.04 installed all right, and now I can boot from it and Windows 7.  I would like to also be able to boot from my restored 12.04, to more easily retrieve settings and bookmarks.  That may mean changing things in GRUB, which kind of scares me.  It may also mean taking my question to another forum.  

Advice gratefully accepted, from someone who feels very dumb right now.
Angela C. Murphy

---

### Post by Bashing-om on 2016-01-04
Angela_C.Murphy; Hey ....

nawwww ..
> 
 from someone who feels very dumb right now.

No one knows everything .. On this operating system of choice, we are all at some point on the learning curve.

As this new development has nothing to do with the original issue now. let's close this thread .
Solved by the application of that nuclear solution - (RE-)install .

In your new thread provide the outputs of terminal commands:
```

sudo parted -l
sudo fdisk -lu

```
We mount the 12.04 file system and pull your files off of it ; If we can not get the 12.04 install to boot .

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by Angela_C.Murphy on 2016-01-04
Thanks to all who replied.  I was lucky.  At some point I made an Ubuntu Boot Repair disk, based on Ubuntu 13.10, from a file downloaded from sourceforge.com.  That disk saved my bacon.  I booted from it and ran the program and now I can boot from both Ubuntus - 14.04 LTS and 12.04 LTS - and also from Windows 7.  If anyone wants to look at all the steps, the URL is  [http://pasteubuntu.com/14405455](http://pasteubuntu.com/14405455).  It is rather long to show here.  I don't know what is wrong with 12.04 and why it did not upgrade properly, but I am very glad I did the backups before trying the upgrade.  That was the only way there was any possibility of recovery from my errors.

My husband and I will continue to use 12.04 until we can transfer settings and bookmarks to 14.04.  We also have to download more software, Skype, Chrome, and GRUB Customizer being just a few.  Meanwhile, even though I am an old lady, I have a lot to learn and have to do a lot of studying.

Again, thanks to all.
Angela C. Murphy

---

### Post by Bashing-om on 2016-01-05
Angela_C.Murphy; :)

All's well that ends well.
Pleased you provided the manner of solution for the benefit of all.

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

