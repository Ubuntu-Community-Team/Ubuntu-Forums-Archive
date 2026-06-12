---
title: "~ Windows UNBOOTABLE BOOT PARTITION Error ~"
date: 2006-05-05
forum: Installation &amp; Upgrades
---

### Post by bennybobw on 2006-05-05
I'm using an IBM Thinkpad t41 and the hard drive decided to die on me last week.  So I got a new blank one.  
I installed windows and then Ubuntu and everything seemed to be fine, but now when I try to boot Windows, the splash screen shows and then gives me a blue screen:
UNBOOTABLE_BOOT_PARTITION
STOP 0x000000ED (Ox896B3710, 0xC000014F, 0x00000000, 0x00000000)

and restarts the system.

This might not be a huge issue, if I had the original XP Recovery CD.  But I don't.  I have the IBM Recovery CD which gives you no control over the process and takes FOREVER.  I can't even boot into safe or recovery mode to run fixMBR.

The thing is, I know that the Windows boot partition IS in fact bootable.  Here's what qtparted says:
01 /dev/hda1 NTFS Active 13.97GB (and GParted says it's got the boot flag) /IBM_PRELOAD
02 /dev/hda2 ext3     -      22.31GB /
03 /dev/hda3 extended      1004.06 MB
  --04 /dev/hda5 linux-swap 1004.03 MB

My GRUB file menu.lst says this about the partition:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

which should be right (and like i said, it shows the windowsXP splash screen, so I know it's accessing the disk correctly).

I don't want to go through installing Windows via the IBM recovery disks again, if I don't have to because it takes hours (and unless you wipe everything, it doesn't reinstall the MBR, which then gives you GRUB errors).

Was this just a random error?  How do I know if I run through the install again, the exact same thing won't happen again?  Help!

---

### Post by scooper on 2006-05-05
Your partition may be flagged as bootable, but it also needs to have a boot sector with a boot program loaded into it.  Grub will do this if you use grub-install or setup from the grub command prompt.

Did you have both drives present when you did the install?  Perhaps the boot loader got written to the wrong drive?

In any case you should be able to do this surgically if you have a LiveCD.  I think the Ubuntu CD has options for booting a command line.  Get help on the boot choice screen or try Ctrl-Alt-F1 after starting the normal Ubuntu install.

From a command prompt you can run grub-install or grub.  Check the info or help, but it may be as simple as "grub-install /dev/hda".  Please, please figure out what your drive really is and double check the documentation, but that may do the trick, assuming the actual partitions are filled with good stuff. :)

Good luck
Steve

---

### Post by bennybobw on 2006-05-06
Perhaps I didn't explain myself entirely.  I have just one [40GB Thinkpad internal hard drive]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-44065").  There is not more than one drive, only other partitions.  I installed microsoft windows onto it and it booted fine, so the whole thing was an ntfs filesystem.  When I installed Ubuntu, I resized the ntfs partition to what you see in my description above, and installed grub on the MBR of hd0,0, where XP is installed.  Now Ubuntu loads perfectly using Grub, but when I try to boot XP, it starts booting (that is, it clearly accesses the correct drive) and starts the boot sequence when Windows, not grub, throws an error.  I've found other people in the forums that have had Grub errors, but not windows errors.  
 
When I originally installed Grub, it recognized that I had WindowsXP.  I loaded up the Ubuntu install CD, and tried to reinstall Grub, but now it does not automatically recognize that WindowsXP is there.

That's why I think something must have gotten screwed up when I resized the drive the first time.  But I don't want to go through the whole install process only to have the same error occur.  Is there something I'm missing about the XP boot process or did the data just get messed up.  I read in [this forum]("http://www.ubuntuforums.org/showthread.php?t=137723&highlight=unbootable+partition"), the following:
> 
First of all, be aware that XP has a funny organizational structure wherein it actually boots from a small FAT32 partition into the NTFS partition. 

I don't know anything about that, but the "hidden partition" sure doesn't show up in any partition program.  I know that tons of people dual-boot xp and ubuntu, so I know it's possible.

Note also that because I have the rescue CDs this thinkpad does not have the "IBM Rescue and Recovery Partition."  On the other hand, I can't acess the Windows recovery console, because I have the IBM rescue disks, not the Original XP cd.

---

### Post by RavenOfOdin on 2006-05-06
This is why I still run GRUB from a floppy after having Ubuntu installed for over three months.

---

