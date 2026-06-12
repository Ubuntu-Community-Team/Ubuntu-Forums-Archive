---
title: "NTLDR is Missing"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by solucki on 2008-03-17
okay, so, I wanted to resize my partitions to give more room in windows where I do all my DVD encoding so I figured I would just delete/reinstall the ubuntu partition and resize them. so I deleted and resized, and then I get a grub loader error, so I get the [super grub loader boot disc]("http://supergrub.forjamari.linex.org/") and it can boot but I wanted to reinstall grub, so I try a couple different things and somehow I erase or copied over the NTLDR.  SO, the recommended path was to repair windows from the windows installation disc.  The problem is when I do that. I get an error that says Hard drive not found.
So, what am I supposed to do now.  I really wanna keep that windows partition, I have a lot files I need in there.

---

### Post by Herman on 2008-03-17
First of all, don't panic.
All your files and operating system is most likely still there, but I don't know what it is you did, so I'm not sure how to help you.
Any clues?

---

### Post by tubasoldier on 2008-03-18
Here are a few options for you:

[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)
[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

They should walk you through the fix.

---

### Post by jimv on 2008-03-18
EZ pho' sheezy

If you can get into Ubuntu, check your XP partition to see if your Windoze files are still there.  If they are, then you're in good shape.  Pop in your XP cd and open the i386 folder.  Copy NTLDR and NTDETECT.COM to the root of your XP partition.  if boot.ini doesn't exist, make a text file and call it boot.ini.  Paste this into it:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=&#8221;Microsoft Windows XP Professional&#8221; /fastdetect

Make sure you change the partition(1) to match the partition number that XP is installed on.

Then update your grub boot entry if needed, to point to the xp partition.

---

### Post by solucki on 2008-03-18
> **jimv said:**
> EZ pho' sheezy

If you can get into Ubuntu, check your XP partition to see if your Windoze files are still there.  If they are, then you're in good shape.  Pop in your XP cd and open the i386 folder.  Copy NTLDR and NTDETECT.COM to the root of your XP partition.  if boot.ini doesn't exist, make a text file and call it boot.ini.  Paste this into it:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=”Microsoft Windows XP Professional” /fastdetect

Make sure you change the partition(1) to match the partition number that XP is installed on.

Then update your grub boot entry if needed, to point to the xp partition.

Thats the problem, I can't get into ubuntu and I can't repair windows because when I put in the win XP disc it says setup is unable to find hard drive.  The only thing i can do is get into the Ubuntu Live CD and I can't get to any of the files on the XP partition.  I need a way to reinstall the MBR and NTLDR. or maybe just the mBR is pointing the wrong direction.  On the super grub disc, I tried the "fix boot of windows partition"
I think that is what messed it up, not sure

---

### Post by jimv on 2008-03-19
Oh, I thought you had access...reading comprehension fails.

If you can't mount your xp partition in Ubuntu, then I'm inclined to say that it's hosed.  It should be mountable even if Windows is broken.

---

### Post by Herman on 2008-03-19
When you boot your Ubuntu Live CD, you could use the command 'sudo fdisk -lu' to see if your partition table looks okay or not.
```
sudo fdisk -lu
```
Regards, Herman :)

---

### Post by linuxtoindia on 2008-03-19
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=728035](http://ubuntuforums.org/showthread.php?t=728035) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				ntldr is missing means you have not removed linux properly ,, so here final attempt is to wipe the hard disk whole!



wait one more thimg , get a boot repair disk from the following here downloads are available...the easiest solution for you!
 [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
 
 [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
 
 [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
 
 [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) 		 	 		  		 			 				__________________thats all ,, chose the best one.. all for free!!:KS

---

### Post by solucki on 2008-03-19
> **Herman said:**
> When you boot your Ubuntu Live CD, you could use the command 'sudo fdisk -lu' to see if your partition table looks okay or not.
```
sudo fdisk -lu
```
Regards, Herman :)

okay, this looks bad, Here's what I get.

a bunch of code, then this:

VFS: cannot open root device "<NULL>" or unknown-block8,1
Please append a correct "root=" boot option; here are your available partitions: Kernel panic - not syncing
VFS: Unable to mount root fs on unknown-block(8,1)


Then it's frozen, no ctrl+alt+del no esc no nothing.  I have to kill the power supply, hard boot it.

---

### Post by jpepin on 2008-03-19
Put in the Windows disk, and be sure to select "boot from CD" on system startup.  Once you boot into the install disk, choose the option to repair the installation (I think it's R).  Once you're in the recovery console, type "fixmbr". Restart to see if it worked for you.   If it doesn't work, try "fixboot".  These fix your master boot record, which I think it your problem.

I've had your issue before, and the above did the trick for me.  Of course, you'll have to reinstall Grub, which is a whole other issue, but at least you'll be able to boot into something :)

---

### Post by Herman on 2008-03-20
Download [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/") or boot your Ubuntu Live CD and install [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") in it, which will remain in the Live CD for as long as you have it booted.
[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") is also available in . [GParted -- LiveCD]("http://gparted.sourceforge.net/") and [System Rescue CD]("http://www.sysresccd.org/Main_Page") .

You should use TestDisk to scan your hard disk for the start points of partitions and use that information to rebuild your partition table for you.
Here is a link to some illustrated examples of how to use TestDisk in case you've never tried it out before, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html").

Regards, Herman :)

---

### Post by Herman on 2008-03-20
> okay, this looks bad, Here's what I get.
a bunch of code, then this:
VFS: cannot open root device "<NULL>" or unknown-block8,1
Please append a correct "root=" boot option; here are your available partitions: Kernel panic - not syncing
VFS: Unable to mount root fs on unknown-block(8,1)
Then it's frozen, no ctrl+alt+del no esc no nothing.  I have to kill the power supply, hard boot it. Did you mean you can't even boot the Ubuntu Live CD?
I thought you meant when you ran 'sudo fdisk -lu' until I your post again.

Maybe you have a hardware problem?

---

