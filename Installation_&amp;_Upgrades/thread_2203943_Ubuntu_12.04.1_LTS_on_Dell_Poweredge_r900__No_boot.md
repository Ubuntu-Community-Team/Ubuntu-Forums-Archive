---
title: "Ubuntu 12.04.1 LTS on Dell Poweredge r900:  No boot drive found after install."
date: 2014-02-06
forum: Installation &amp; Upgrades
---

### Post by johnodonovan on 2014-02-06
Hi,
This is my first post here.  (Thank you all for the really great info on this forum, it has helped many times!). 

I have some familiarity with Ubuntu, but I am stumped by this problem:

Ubuntu 12.04.1 LTS, fresh install from cd on Dell Poweredge r900 rack servers with 4 300G drives.  (These machines had Windows Server 2008 installed at one point in the past) The Ubuntu install worked on 2 of 3 servers.   On the third one, the only difference was that hardware RAID was set up, so that one virtual disk was seen by the os.   I can boot into ubuntu server from cd and perform the install with no errors.   However, I get a standard "no boot device found" error on boot.  For the other two machines, I had to modify grub to include a delay in grub to achieve a clean boot  (bootdelay=90 nomodeset) and then run update-grub.  I believe this is to allow the poweredge devices time to respond, otherwise they would drop to INITRAMFS during boot.  

I have tried the following, to no avail:
Undo all RAID settings from the LVS Adapter interface  (now os can see 4 drives)
Removed all partitions from all drives, through partition manager in kubuntu live cd   (data already backed up, moved etc)
Ran ubuntu server cd installer successfully with network connectivity. 
Still got error, so booted into Live CD, installed and ran BootRepair facility --It finished with "boot repaired successfully" and the output is available here:

[http://pastebin.ubuntu.com/6882050/](http://pastebin.ubuntu.com/6882050/) 

I am able to mount /dev/sda1 and read write with no problems, so i am not convinced that the drive is corrupt  (to be sure, I also phyiscally swapped two of the drives and redid the entire install process described here, with the same result)
Still no dice :(

I hear there are issues with older Dell bios versions not setting boot flags correctly for Ubuntu, but fdisk -l shows that there is a flag.
From my (first time user) interpretation of the bootrepair log, I think it might be something to do with the path that core.img is pointing at?
Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],msdos1[COLOR=#666666])[/COLOR]/boot/grub on this drive.

My BIOS version is from 2008, and Dell do have an "urgent" install from 2012, but I am reluctant to reinstall the Bios because it seems to be in .exe only, so I will have to go boot some sort of MSDOS environment, which is really unfamiliar to me.   --I will do this based on feedback I get here if it turns out to be important. 
Any insight / advice is really, really appreciated!   (i.e:  someone please tell me my hardware is fine and I'm just missing a semicolon somewhere :)
Cheers.

---

### Post by johnodonovan on 2014-02-12
Anyone ??  Im still stuck on this :(

---

