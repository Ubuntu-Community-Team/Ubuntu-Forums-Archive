---
title: "Howto: Multiboot Windows XP, Windows Vista, Ubuntu 6.06, etc"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by 3370318 on 2006-09-19
There does not seem to be a very good (or at least very accessible) discussion on how to independently (by this I mean not simply chaining boot loaders) multiboot Windows XP, Windows Vista RC1, Ubuntu, and other distros.  As such, I would like to share my method for accomplishing such a setup.

My setup uses multiple partitions on a single hd as follows:
Boot Manager – XOSL (on a dedicated partition)
[INDENT]Windows XP
Windows Vista RC1
PC-BSD
Ubuntu 6.06[/INDENT]

I chose XOSL because it is very convenient to reload from a dedicated partition, it doesn't mess up the MBR, and it looks snazzy.  However, getting Vista to work with XOSL, Linux, and Windows XP is surprisingly difficult and requires several steps.

Recommended:
Download and burn a copy of the “Ultimate Boot CD” from [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) as it has a ton of useful tools for partitioning, booting, and diagnostics in a very convenient package.  All of the packages that I used (for example, Ranish Partition Manager and XOSL) are all on this CD.

Step 1:
Partition your HD with whatever partitions will be needed prior to installing Vista.  I found that Ranish Partition Manager is a wonderful tool this purpose; however, it is text-based.

Step 2:
Install Windows XP (if you don't have it yet)

Step 3:
After Windows XP is installed and configured, reboot and use Ranish to set Vista's partition as active (B for boot in Ranish).  I would discourage trying to set the partition active through Windows (setting it active through Windows destroyed my extended partition for that HD).

IMPORTANT:
This step is very important as Vista will otherwise modify the contents of whichever partition is set active; most of the time, this seems to be the partition belonging to Windows XP.  If this situation occurs, Vista will store bootmgr and BCD (two all important files without which Vista cannot boot) on the Windows XP partition, NOT on the Vista partition.  In this case, Vista will be incapable of directly booting through any other means (not through XOSL, not through GRUB, not through ANYTHING).  At this point, Vista is irrevocably tied to the XP partition which cannot change in a manner that would alter the loading of bootmgr.  Also, if Vista's boot sequence is altered even slightly (say by installing XOSL) Vista will probably fail to load correctly as will other detected Windows (aka Windows XP) installations.  If you choose to run fixboot from the Windows XP recovery, then Vista will no longer load bootmgr and will no longer boot (at this point there is no way to repair Vista).  This situation should be avoided.

Step 4:
Install Vista.  At this point, you'll need to select a partition to format with Vista's implementation of NTFS.  Note that this is a newer NTFS version and cannot be correctly resized with standard Windows tools or other tools such as qtparted.

Step 5:
Install XOSL or whichever boot loader you prefer.  If you are unable to install XOSL through UBCD, try saving the files on a FAT32 drive and run the installation from there.  I have found that storing XOSL on its own partition saves headaches later on.

Step 6:
Set up XOSL to list Windows XP as one choice and Windows Vista as another.  At this point Windows XP will probably load correctly through XOSL, but Vista will not.

Step 7 (Repair Windows XP if it doesn't load through XOSL):
At this point, Windows XP and Vista may not load correctly.  To fix the problem with XP, use XP's installation disk to get into the recovery console.  Once the recovery console is available, run fixboot (do not run fixmbr as this will overwrite the link to XOSL) and be sure to specify the drive that XP is on (probably C).  Vista's drive should also be listed among possible choices, but it will probably some higher letter (like G).

Step 8 (Repair Vista):
Use Vista's installation disk and choose the repair option.  It will probably detect that something is wrong, attempt to automatically repair itself, and then ask if you would like to reboot.  Do not choose to reboot (the automatic repair doesn't really work).  Instead, continue on to the next repair screen and choose the option to repair Vista.  If you observe the log file from the repair, it should note that it edited the booting options (toward the end of the log file) and will probably mention BCD.  At this point, you should be able to reboot.

Step 9:
Verify that you can indeed boot into both XP and Vista through XOSL without going through any additional boot managers.

As an aside, Vista may boot correctly, but may fail when it actually tries to display the user login (perhaps it assigns a refresh rate out of the range of your monitor).  If this is the case, you can press F8 whenever you first boot Vista from XOSL for more options (such as 640x480 resolution) which may be helpful for resolving such errors.  Once everything is correctly working, install Linux.

Step 10:
Install Ubuntu onto whichever partition you prefer (note the partition that you choose to format and mount as /).  Go through the typical installation procedure until you reach the point of installing the boot manager (grub).  Instead of installing to the MBR, choose to install grub onto the root partition (/dev/hd*whatever you decided to format as /*).  For example, I installed grub on /dev/hda6, the same as my root partition for Ubuntu.

Step 11:
Set up XOSL to list Ubuntu as another choice.

Step 12:
Install any other OSes you want using the same method as Ubuntu if they are *nix based.

If everything worked correctly, you should be able to boot Windows XP, Windows Vista RC1, Ubuntu, and anything else directly through XOSL without any difficulty.

Note:  You could choose to install XP, then Vista (ignoring Step 3), then Ubuntu and install grub onto the MBR.  This setup works, but in order to use XP, you must first choose “Windows XP Professional” through grub and then choose “Legacy Operating System” through Vista's boot manager.  Also, as noted in Step 3, any change to the booting method on the XP partition will destroy your capability to boot Vista.

Hopefully this will save somebody some headaches and time.

---

### Post by pay on 2006-09-19
This would probably be easier to fing in the HOWTOs, Tips & Tricks section

---

### Post by 3370318 on 2006-09-19
That's a good point.

---

### Post by Giraffeicles on 2007-10-07
I also like XOSL but I am a bit of a throwback, I like dos too!

So my first partition (1G) is DOS, xosl and alot or other things.
My second partition is Vista (60G).
My third is XP (50G).
My fourth is a logical that contains, 29G empty (hmm, what to put in here), 50G Gutsy, 2G Swap.

I can boot dos, vista, xp no prob, using XoSL means none can see any of the others, isn't hiding great.

But I'm stuck getting the grub into the 20G /.  Because Gutsy just chucks it in the mbr without asking (or I'm not reading the question correctly).

I'm assuming I'll need to boot from the cd and get to a prompt, now it's time for google.

I've got to use gutsy tho as 6.06/7.04 can't see my hdd/cd drives.  Serves me right for getting new stuff.

Just wanted to add my ten cents worth.:)

---

