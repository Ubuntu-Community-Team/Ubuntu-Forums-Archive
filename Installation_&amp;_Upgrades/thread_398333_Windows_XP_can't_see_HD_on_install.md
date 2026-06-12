---
title: "Windows XP can't see HD on install"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by flooperer on 2007-03-31
I installed feisty, that's fine, works well, still no wireless but that will come.

But. I need to run some apps that only come for windows, so I need to reinstall windows XP.

But when I boot off the Windows XP disk it flatly denies that there is a hard drive in my computer. It's a compaq V3000, it has a fujitsu 80gb sata drive in it.

I have tried to reformat the drive using:

Dos fdisk booted of cd

Gnome partition editor (booted off ubuntu edgy and feisty CD)

Ubuntu fdisk , booted off CD

Symantec ghost booted off network

dos fdisk booted off floppy

Darik's Boot and Nuke booted off CD


Even after all that when I run windows xp setup I get the message:

Setup did not find any hard drives installed in your computer.

The drive is functional, I can install ubuntu on it and it runs fine, but whatever I do I can't get windows back on it. 

It seems like ubuntu put something on the start of the drive that nothing can remove?

I will be grateful for any ideas. Thanks, Matt

---

### Post by IanGB on 2007-04-01
Well I have never had a workable answer to this one either Flopperer

---

### Post by pradeepadapa on 2007-04-01
why dont u go into ubuntu fiesty nd install gparted graphical gnome partitioner software nd partition the drives with NTFS or VFAT so that ur windows detects these drives nd ur HDD again

---

### Post by flooperer on 2007-04-01
That doesn't seem to work. I've tried NTFS and FAT32, but Windows setup just won't have anything to do with it. I think there is something up in the MBR, I've tried deleting the MBR but that doesn't help either.

---

### Post by pradeepadapa on 2007-04-01
then why dont u repair or reinstall the MBR on ur hdd from the windows xp cd using the repair function nd from the command line

---

### Post by frodex on 2007-04-13
I'm having this excact same problem, new HP laptop with 100gig SATA drive with a partition reserved for XP that the install CD just can't see whatever I do. Judging by this thread, outlook isn't very good either..

---

### Post by flooperer on 2007-04-13
Hi Frodex,

I ended up bringing it back to the store, they couldn't fix it either, but they sent it back to HP and they did fix it. I don't know how, or what, they did to fix it unfortunately, but it works now!

I guess the moral of the story is to partition before install for best results!

Good luck!

---

### Post by charles nicholls on 2007-04-13
The problem is that Xp wont recognise the sata drive without the sata driver.
When you start to load xp you need to press F6 at the prompt and load the driver
 from Floppy. ( the driver should be on the motherboard disk or you can download it if you know the chipset)
hope that helps

---

### Post by frodex on 2007-04-16
After some searching I too found that it was the SATA disk that was the problem.  In my case the fix was very easy, I simply disabled 'Native SATA mode' in bios and XP install could see the disk!

---

