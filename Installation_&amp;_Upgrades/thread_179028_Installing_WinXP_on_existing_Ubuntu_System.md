---
title: "Installing WinXP on existing Ubuntu System"
date: 2006-05-18
forum: Installation &amp; Upgrades
---

### Post by Paradoxdruid on 2006-05-18
I currently use a [System76]("http://www.system76.com") Koala Mini as my media center of choice, but for various reasons want to dual-boot into WindowsXP.  (The Koala rocks, btw, and System76 was a great company to do business with).

I downloaded a GParted liveCD and shrunk my existing ext3 main partition, and created a 20 GB FAT32 partition for Windows.

I haven't actually tried putting the XP install disk in yet, because I'm hoping someone will have relevant experience (though a quick search didn't reveal any guides out there).

Does anyone know if Windows will ignore the first partition (ext3) and install onto the second partition (FAT32)?  If so, I assume it will destroy the MBR anyway.

What's the best way to save my current GRUB boot record and restore it after Windows installation (and add WinXP to the menu?)?

To clarify the situation:  The system is a mac-mini size factor.  So it has one harddrive, a CD slot, and not much else.  No floppy drive, no option to add additional internal harddrives, etc.

Thank you in advance for any help!

---

### Post by kevinlyfellow on 2006-05-18
I had a friend who needed to reinstall windows on a comp which had an extra partition in it (not linux though) and did not destroy it.  It was even an oem disk.  I don't _think_ it will write over any partitions except for one (I would put the windows partition at the begining of the disk but I'm not sure if it matters).

Down to what I really know.  [URL="http://www.ubuntuforums.org/showthread.php?t=24113&highlight=HOWTO+Restore+GRUB"]
Check out this HOWTO 
[/URL]

This MBR restoration method has worked for me when all else failed.

btw, sweet box... how do you like it?

---

### Post by crichell on 2006-06-08
For anyone interested we've put together a How To on adding Windows to an existing Ubuntu installation.  The article assumes Ubuntu is the only OS on your hard drive.

[http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

---

