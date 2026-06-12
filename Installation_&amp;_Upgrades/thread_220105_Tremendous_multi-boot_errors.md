---
title: "Tremendous multi-boot errors"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by jgclark123 on 2006-07-21
I know that this isn't mainly an Ubuntu error, but it does involve Ubuntu, and I have nowhere else to go.  

About my hardware:
CPU: AMD Sempron 3400+
RAM: 2x 512 MB Corsair Value Select
Mobo: some Gigabyte Socket 754, I can look it up if it'll help
Video Card: just upgraded from an nVidia 32 MB MX400 to an ATi 256 MB X1600 Pro (pretty big upgrade, huh?)
Hard drives: (Here's where it gets complicated.)
[INDENT]Channel 0, Master: 10 GB[/INDENT]
[INDENT][INDENT]9 GB NTFS, with Windows XP SP2 (Drive letter C)[/INDENT][/INDENT]
[INDENT][INDENT]1 GB Linux Swap[/INDENT][/INDENT]
[INDENT]Channel 0, Slave: 40 GB[/INDENT]
[INDENT][INDENT]33 GB NTFS, no OS (Drive letter N)[/INDENT][/INDENT]
[INDENT][INDENT]7 GB Ext3, with Kubuntu 6.06 (Drive letter K)[/INDENT][/INDENT]
[INDENT]Channel 1, Master: CD-RW[/INDENT]
[INDENT]Channel 1, Slave: 6 GB[/INDENT]
[INDENT][INDENT]6 GB NTFS, Windows 2000 on it, but I don't use it (Drive letter E, under XP)[/INDENT][/INDENT]
[INDENT]Channel 2, Master (SATA): 300 GB[/INDENT]
[INDENT][INDENT]275 GB NTFS, just installed XP Pro SP2 when issues arose (Drive letter D)[/INDENT][/INDENT]
[INDENT][INDENT]25 GB Ext3, empty (Drive letter L)[/INDENT][/INDENT]
All drive letters under Windows XP.  (I have an Ext3 driver, which is why the Ext3 partitions have drive letters.)  


I bought a new SATA hard drive off of NewEgg, and decided to give my old hunk-of-junk 40 GB drive to my step-dad.  I wanted to migrate everything over, when I realized that I didn't need to keep everything in RAR and 7Z archives anymore for space.  (This is in Windows XP:) When I tried to unpack them, any file over about 300 MB in size would give me a disk probably full error in WinRAR, or a file is broken error in 7-Zip.  I thought that the hard drive was corrupted, so I ran CHKDSK in Windows XP, and it returned no errors.  Then I tried to extract one of the archives from the old hard drive to the old hard drive, and I was met with the same error.  This ruled out corruption of the new hard drive.  The archives had worked before, so I don't know what went wrong.  Sadly, I don't have any backups of the archives to compare the checksums.  They may have somehow become corrupted, but only large files give me errors, or extracting a number of files at the same time from one archive that exceeds about 300 MB (individually extracing works fine).  Also, I could workaround with the RAR archives by converting them to self-extracting archives in WinRAR, but this cannot be done with 7Z archives, neither in WinRAR nor in 7-Zip.  

This led me to believe that when I installed my new Video Card, Hard Drive, and TV Tuner all in a matter of two days Windows had a major issue and is at fault.  Because I decided that the error must be with Windows, I decided rather than copy my old install over, I would start fresh, and hopefully fix the problem.  

Well, my install was fragile, to say the least.  The bootloader was on the C: drive (Channel 0, Master, Partition 0), and it called GRUB on the K: drive (Channel 0, Slave, Partition 1).  So when I installed Windows XP on the D: drive (Channel 2, SATA) it must have fooled around with the bootloader on the C: drive, while not putting a bootloader on the D: drive.  Now I cannot boot into any OS, and I'm writing this from my Kubuntu 6.06 Boot CD (or Desktop CD, whatever).  (Actually, I haven't tried the Windows 2000, but that was installed on a different computer [Pentium III] so it may not work...  After I post this I'll try that.)  

Anyway, I know that this has little to do with Ubuntu, but at the same time, it has about as little to do with Windows.  The problem is the annoying concept of bootloaders, and I have nowhere else to turn beside the helpful, intelligent Linux crowd.  Any suggestions to fix any of my many problems would be *greatly* appreciated.

---

### Post by nalmeth on 2006-07-21
WOW

that is one tangled mess you're in :p

Start off [restoring GRUB]("http://doc.gwos.org/index.php?title=Restore_Grub&printable=yes"), and try to reorganize the thread if you can, it's complicated, and a little difficult to read.

---

### Post by jgclark123 on 2006-07-21
Indeed it is complicated, but I don't know what else to say, or how to shorten it without losing important information.  

Restoring GRUB sounds like a plan, I'll have to look that up; I know I've seen it somewhere around here.  Anyway, if I restore GRUB (which I believe is done via boot CD, luckily) will that give me access to my Windows partitions as well?  If it doesn't that's okay, I can install an NTFS read/write driver in Kubuntu and try to manually restore the NTLDR.  

I'm going to bed now, but in the morning I'll be sure to get cracking on this.  Thanks, nalmeth, for the help.  I hope it works.  I will definitely post my results.

---

### Post by jgclark123 on 2006-07-21
Couldn't sleep... I just restored GRUB, and now I'm going to reboot, and first see if I can get into Windows.  If that doesn't work, Kubuntu.  Finally if all else fails, Boot CD again.  

What worries me is how this happened.  I had an old hard drive in an external enclosure that recently started acting up.  I hope it didn't have a virus.  That was when this all started, but so was my new video card, TV tuner, and hard drive.  (Graduation gift money; big families rock!)  At least in Windows I'll know what I'm doing so I can try some anti-virus programs.  I really hope to get into Linux more, but I guess I'll get there over time.  

Thanks again, and if I don't post again soon, that means I've made it to sleep.  ...or my computer is completely fried...

---

### Post by jgclark123 on 2006-07-22
Wow, it's been a while... anyway, I never did manage to get GRUB restored correctly (Error 21) so I just worked on getting Windows bootable first.  I managed to, with some helpful DOS-based floppy utilities, get NTLDR, NTDETECT.COM, and a BOOT.INI on my SATA drive, and that did get me into Windows... for about a second and a half, then it blue-screened.  The BSoD said that it was a hard drive or hard drive controller error, so I should virus scan and run CHKDSK.  I had already run CHKDSK once, so I decided to virus scan with F-Protect and McAfee.  Neither turned up anything and that took most of the day.  (I like to sleep in.)  Now I'm running CHKDSK again, and hopefully it will magically solve my problems if it ever finishes.  (I'm using my step-dad's computer right now.)  If this doesn't work, I'll try a different SATA port on my motherboard.  If that fails, a PCI SATA controller.  And if that fails, I'm RMA-ing my hard drive back to NewEgg, losing plenty of data that I can't back up without wasting endless CD-Rs or buying a new hard drive.  

...I may need to remove my Kubuntu partition to make room for Half-Life 2 before I ship off the new drive.  My new video card works just fine...

---

### Post by jgclark123 on 2006-07-22
Well, no dice.  It's not a virus.  It's not a faulty SATA controller.  It's not a faulty SATA cable.  

I don't know if I should RMA it back to NewEgg because I can't get my old Windows drive to boot either.  It used to say that NTDETECT was missing.  I replaced it, and now it just freezes on a blank, black screen with the gray cursor (text cursor, not mouse) in the upper left corner of the screen.  I have to cut the power to reboot.  

I guess my next cure-all end-all will be to reformat each drive one-by-one and try to reinstall Windows or Linux or whatever on each one to see if I can get anything working.  I should start with the 10 GB.  I can back it up with a DOS utility onto the 300 GB drive.  (Thank you, NTFS4DOS.)

---

### Post by Herman on 2006-07-22
As far as your booting problems go, I would recommend GAG Boot Manager for booting Windows, especially.
It is a real lifesaver for those of us who like to unplug hard disk drives and switch them around,  or install and uninstall operating systems often.
GAG Boot Manager is very fast and easy to reconfigure, and can be run from a floppy disk, a CD, or installed to MBR if you want.

To get GAG Boot Manager to boot Linux, you still need to have either GRUB or LiLo there for it to chainload. You need to install GRUB or LiLo to the first sector of the Linux partition. (Instead of to MBR). There are lots of ways to do that. 
1) You can install GRUB or LiLo anywhere with the 'Rescue a Broken System' Mode with the Ubuntu Dapper 'Alternate' Install CD.
2) Or open a terminal in Ubuntu Dapper 'Desktop' Live/Install CD, get a Grub Shell and install Grub to your Ubuntu partition.

If you can boot with GAG you might not need to re-install all of your operating systems, and it will be a very useful piece of software for you to keep and use again someday in the future. 
For a web page about how to use GAG Boot Manager, **[*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm")**.

---

### Post by SkyNet2029 on 2006-07-22
The 'disk probably full' errors are usually due to a temp folder being, umm. full. 
Basically, since you said anything over 300MB pops this error, I would say go into your internet settings in Xp and change the size of our Temporary Files folder to something larger than the 300MB threshhold you keep hitting.
I know, sounds kind of dumb, but that's what happens when you integrate a fie manager with a browser.

Since this box only really has four booting slices, and all of your woes started after the XPsp2 install, you probably had your MBR overwritten by the XPsp2. 
For quick access to the NT side at least, you could just go in with an install cd for your XP and go into the recovery console.
Then type FIXMBR <ENTER>
Then type FIXBOOT <ENTER>
which should give you XP access. From there I say get a more universal rescue floppy, like this one from this site :
[http://www.tux.org/pub/people/kent-robotti/looplinux/rip/]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip/")

which in turn allows you access to the drive and all partitions.
it's a small linux system for times like these.
Good luck.

---

### Post by jgclark123 on 2006-07-22
Well, I've been able to restore GRUB using the command line.  Earlier I had tried the install Ubuntu partway, but don't format anything approach.  Now I have GRUB and can boot into my Kubuntu partition, but I think that I screwed it up because I can't get past login.  It has my username filled in, I enter my password, and hit "Enter".  It begins to log in, but a second or two later it returns to the login screen.  

As for booting into Windows, my old, modified GRUB menu is back, but it's not much help.  It still points to the correct place for Windows XP, but it won't load.  I does correctly chainload to Windows, but the failure seems to be in Windows.  Because my MBR is pointing to GRUB as I want it to, does this mean I should use the Recovery Console on the old Windows XP installation and FIXBOOT, but not FIXMBR?

Edit: 
Thank you, Herman, for the link to GAG Boot Manager.  I'm going to make a floppy for backup right now.  

Thanks also, SkyNet2029, for the thoughts on the TEMP folder.  I just realized that my TEMP folder is on my smaller 10 GB hard drive, which is more full now than it has been in the past, which is why I could extract the files earlier but can't now.  It was such a minor issue, but it has caused me to lose access to Windows, and learn that the boot sector of my new SATA drive must have some sort of error.  

So, to reiterate, should I FIXBOOT my old Windows XP installation to try to get it working again?  I believe my MBR is fine, now.

Edit2:
I tried FIXBOOT, but to no avail; I am still unable to boot into Windows.  I'm going to check some Microsoft forums, and hope that I can find an answer.

---

