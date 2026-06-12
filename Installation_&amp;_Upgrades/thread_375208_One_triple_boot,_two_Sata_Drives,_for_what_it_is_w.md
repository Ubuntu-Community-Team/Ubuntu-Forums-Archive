---
title: "One triple boot, two Sata Drives, for what it is worth."
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by BillZog on 2007-03-03
Thanks to "GAG" I have finally been able to do a triple boot of WindowsXP, Ubuntu, and a copy of Xandros that I have had around for three years (that I added for comparison purposes). I'm now more than three weeks into the triple boot system and all is working well, though just to stay safe I am still using a GAG floppy to boot.  Here is my experience:

Installing for Dual or Triple Boot on 2 SATA Drives wasn't easy. Took 4 tries and two clean installs of XP.  Setup = 3G Pentium 4, 1008 Memory, and two SATA Drives, one original 80G Seagate, the other a new WD 250G. 

The SATA drives do not have &#8220;master/slave&#8221;  jumpers, but my intel D865GBF motherboard has two SATA Ports and BIOS assigns the drives they are connected to as HD0 and HD1 in its BIOS>Advanced menu (though allows either drive to be designated as "1st Drive" or "2nd Drive" in BIOS>BOOT>HARD DISK DRIVES menu. (This, plus "Grubspeak" drive counting, "LinuxSpeak" drive counting, and "SATA vs IDE Speak" drive designation, made the installation process especially interesting.)

_Try One_ was an attempt (via Ubuntu Alternative iso CD 6.10)  to let Ubuntu takeover the old 80G drive (HD0, HD1 or sdb, as above) and keep a new, clean install of windows on the new 250G drive (sda). My  first mistake with this try was to let Grub overwrite the MBR of Drive One when, during installation, the Alternate Disk (6.10)  suggested it. (I think GRUB also had a problem deciding which drive was which. ) I ended with a good boot of Ubuntu, but nada for Windows XP.  SuperGrub disk would not help and for some reason my Windows XP boot floppy couldn't find the Windows drive. My second and bigger mistake with this installation attempt was my giving up too soon and reinstalling windowsXP.  (Later I learned that Gag, Knoppix, SystemRescueCD, or a little program called "NTLDR is Missing" might have helped.) I also think that using Partition Magic to format, resize, partition, and remap the drives,  especially the drive targeted for Linux did not help and might be why the Windows Boot Floppy could not find the "C" drive.

_Try Two_, disconnecting the cables to the 250 G drive on Motherboard Port 1 (Windows) while I installed Ubuntu on the 80G (MB Port 2) sounded great on the Forum pages, but did not help. Oh yeah, Ubuntu worked fine, as long as it thought it was on "sda." When I reconnected the 250 drive with Windows, Ubuntu would no longer boot  (because it was now "sdb") meaning when I tried to use BIOS to control booting sequence of the hard drives, the Grub menu would show up but would not boot.  There were two "Catch22's" here: 1. the main reason I was trying to install Ubuntu was to learn more about Linux, yet the installation process required at least fair knowledge of Linux; 2. Even if I learned enough "Linux speak" to change things, I couldn't figure a way to edit the files I needed to edit to put things right (like /boot/grub/menu.lst)  without already being in Linux.

_Try Three,_ was when I first discovered GAG and with it I was able to successfully dual boot with Windows on Drive 1 and Xandros on Drive 2. It's a simple and great bootloader as far as I am concerned. Installs easily, very intuitive,  runs equally well booting from floppy or from hard drive and is simple to Uninstall if needed. My mistake in try three was using GParted to pre-format the second half of the 80G sdb drive before installing Ubuntu via Alternative Disk 6.10. Somehow I screwed up (again) and the installation process failed because it could not find /root.

_Try Four_, worked like a charm. I used GParted to delete my empty preset partitions on the last half of Drive 2 and let the Ubuntu Alternate 6.10 disk handle the partitioning, though I  did not let the installation process overwrite either MBR with Grub. In fact Grub would not install on the needed partition (hd2,4  "Grubspeak") so I used the option to install Lilo on (sdb3), actually the same location. When I created a GAG boot 3 1/2 floppy (rather than installing it on the hard drive just to stay safe) and I added separate boot options for Windows, Ubuntu, and Xandros all finally began to click. Later, I installed GAG on the hard drive, then uninstalled it just to make sure I could.

Kudos to the following websites and/or applications that helped me along the way:

HERMAN'S SITES: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) - for a whole lot of information 

PSYCHOCATS: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)  - for concept and more information

TESTDISK: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) - to read the disk and partition structure on both drives

 EXPLORE2FS:  [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm) - to read the Ubuntu directories and files from windows before Ubuntu itself would boot.

AND, SUPERKUDOS TO: GAG. [http://gag.sourceforge.net/](http://gag.sourceforge.net/) - for the program that gave me the key to open the doorway.

Now I need to get on with learning something about Linux commands and Ubuntu specifics.

BH

---

### Post by Herman on 2007-03-03
Hello BillZog,
Welcome to Ubuntu and thank you for the interesting story of how you did it.
All the best, Regards, Herman :)

---

