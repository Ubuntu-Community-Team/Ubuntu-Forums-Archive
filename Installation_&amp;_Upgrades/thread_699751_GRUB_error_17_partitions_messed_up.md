---
title: "GRUB error 17: partitions messed up"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by NiceInVT on 2008-02-17
First of all I scoured this forum for "GRUB error 17" and the answers did not seem to match what I am seeing.

Ubuntu 7.10 install on a Dell 1720 Inspiron went 100% ok 2 months ago.  Today I pressed the little circular "home" button next to power on the laptop....BAD IDEA!  Windows started installing something ... power button didn't work, I panicked, unplugged system.  Upon next reboot, GRUB error 17 results.  So I can't boot hda1 partition (original boot partition) anymore.

Booting into Ubuntu 7.10 LiveCD, running terminal window:

```
sudo fdisk -lu 

Device           Boot     Start  End    Blocks    Id     System
/dev/sda1      *              --    --       --          c        W95 FAT32 (LBA)
/dev/sda2                      --    --       --         5        Extended
/dev/sda5                      --    --       --         82     Linux swap / Solaris
```

Looks like whatever fancy schmancie thing windows tried, it changed the file system from ext3 to whatever the heck W95 FAT32 (LBA) seems to be.  So now I'm panic'd, wondering if windows actually wrote anything to my sda1 partition.   

```
sudo mount /dev/sda1 /ubuntu 
```

This command works well, sda1 becomes mounted to /ubuntu.

```
ls /ubuntu

boot.ini    CLLauncher.exe   hiberfil.sys   md3.txt      pagefile.sys   version.ini  WERUNTIME.INI
bootmgr   DOCUMENTS AND SETTINGS  MD2Fixer.exe    ntdetect.com   Program Files  Welcome Pictures windows 


```

Now I pretty much freak.  Looks like /sda1 now only has these windows files and folders on it!  I don't know why or how but I can't see any old linux files or the root /.     I have tried using Super Grub to no avail.

Can anyone tell me if (1) the sda1 partition is overwritten and unrecoverable now and (2) is there a way to get back my linux system?

---

### Post by Pumalite on 2008-02-17
[http://ubuntuforums.org/showthread.php?t=417761](http://ubuntuforums.org/showthread.php?t=417761)
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by dstew on 2008-02-17
Wow, bad thing. Do you know exactly what that button was? You are referring to a button on the keyboard, right? That is, it was not a menu item on the desktop.

You should probably be looking for programs that try to repair partitions. [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") is one that comes to mind.

EDIT: I checked out the "House" button. Apparently, pressing this button causes the BIOS to load a small, independent operating system from a "Media Direct" partition that was originally present. Its purpose is to allow a user to quickly enable media programs because it takes so long to load WIndows. I don't know exactly how to explain the behavior you saw, but my guess is that when the Media Direct key was pressed, and the BIOS did not find the operating system it expected, it might have tried to "repair" the Media Direct partition, which, of course was now your /dev/sda1. But maybe your partitions are intact, but only the partition table was messed up. Anyway, TestDisk seems in order here.

---

### Post by BoomShaka on 2008-03-02
Sigh. I've had the exact same problem also on the dell 1720.
I held down the custom "Home" button while booting up (don't ask me why). I powered off when I realised Dell Media Direct was doing something nasty to my drive. Upon reboot... GRUB 17 error... seriously, thanks for asking me if you can reformat my drive dell... :mad:

Using the live cd, I found to my dispair, it had actually gotten as far as writing some crap to my drive (Program Files, WINDOWS, etc folders) and changed the filesystem.
I doubt I have much chance of recovering my data since it got this far, so I am starting my reinstall now. Luckily most of my data is backed up on external drives.

The main annoyance of course is having to fix all the bugs that I originally had to battle with.

Anyway, if you know of a way to disable that rubbish and remove it from the system entirely, let me know.

---

### Post by neonard0 on 2008-03-10
Same happend to me, but I could "repair" the system, well the truth is that the pc itself got repaired:

The stage was this:
First I installed Xp (c:/), then Installed Vista(d:/), then installed ubuntu (Other partition and other for swap)
Everything was perfect, but one night trying to start my xp1330 accidentally I push the HOME KEY. , the logo of dell media direct appear and then and BLUE error screen with message (common functionally of windows) told that there was a mess with the system. I could not restart the pc, it was blocked, so I kept the start button pushed to restart, the grub appear, but when I selected the menu for booting on vista or Xp, the system showed the same error, fortunatelly i could boot from ubuntu, but once in it the partitions were not mounted, after checking with fdisk from a booting cd, It showed that the C:/ partition was moved, now for a emty partition with just like 2Gigs, the d was there but not mounted too, and the format was not showed.
Well I was about to format everything but then a friend of mine appear, so to show him what no to do (I mean if you have a shutdown dell notebook YOU CANT PRESS THE HOME KEY) so as the system was messed up, I press the key once again, The direct media logo appear ( as If I have started the pc with the power on button, and select the vista option to boot) and the It show me the grub menu, it was strange because the the graphics was ugly, so I select the Vista option to boot. MIRACOULUS AND HIBERNATING XP WAS STARTING and then i was on XP, I restarted the machine and select the vista option again, then appear normally the next boot menu (the vista menu, to select vista or XP start), everything worked fine, then I restart and go into ubuntu and the partitions were mounted normally.

So I dont know If you people tried to start the pc with the home button, that was my case and know I'm writing this down in case someone want to try this. I dont want to test that, maybe i just was lucky

I forgat to say that when I saw the media direct image when booting I inmediatly stop the machine, lefting the power on button pressed. so after restart the system gave me an error. and then i did the above

---

### Post by Dithers on 2008-03-11
I posted this in another thread, but I just want people to find it
I found nothing helpful when it happened to me and I don;t want anyone else to have to reinstall

To fix the grub 17 error "caused by media direct" and put everything back exactly how it was without reinstalling anything

[COLOR="Red"]boot your computer with a Knoppix live CD[/COLOR] "does not work with ubuntu live cd"

in terminal run

[COLOR="Blue"]sudo fdisk -lu[/COLOR]

[COLOR="Red"]check the name of the partition that was changed to fat32[/COLOR] "may be different in knoppix"

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/hda1   *          63   153693854    76846896   c  W95 FAT32 (LBA)[/COLOR]
/dev/hda2       153693855   156296384     1301265    5  Extended
/dev/hda5       153693918   156296384     1301233+  82  Linux swap / 

[COLOR="Blue"]sudo fdisk /dev/hda[/COLOR] "or HD name"

[COLOR="Red"]Command (m for help): m[/COLOR] "Type m for menu or just type t"

[COLOR="Red"]Partition number (1-5): 1[/COLOR] "type partition number"

[COLOR="Red"]Hex code (type L to list codes):[/COLOR] "83 for linux or l for list to choose"

[COLOR="Red"]Command (m for help): m[/COLOR] "type w to write to partition or type m for list"

changes will not take effect in knoppix, restart and your ubuntu will start as normal with no grub 17 error

---

### Post by SinusX on 2008-03-14
Hi,

I'm a brand new Ubuntu user and just installed 7.10 on my Dell xps 1330 five days ago. I had the exact same grub error 17 as mentioned in the first post here after Media Direct tried to boot when I hit power on. Just want to share my path to a solution - an experience from an Ubuntu-novice in other words.

The solution turned out to be to hit the Media Direct button instead of power on while trying to reboot after the Grub error and Ubuntu booted! Just like someone described above.

The first time I had the error (a couple of days ago) I didn't know anything about the existence of Media Direct. After trying to understand different guides to fixing Grub errors for hours I gave up an reinstalled Ubuntu. 

I used these among others, and although I didn't figure out how to fix my error, I learned a lot from them:
[http://ubuntuforums.org/showthread.php?t=442945]("http://ubuntuforums.org/showthread.php?t=442945")
[https://help.ubuntu.com/community/LiveCdRecovery]("https://help.ubuntu.com/community/LiveCdRecovery")
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17")

But then the error returned today.. again I tried different guides to Grub errors (including boot from the Live CD, Super Grub Disc, weird commands in the terminal etc.) but they were all to complicated for me as a new user and for this reason didn't work as expected. Most of the solutions I could find were primarily relevant for dualbooters and more than one HDD owners. During these failed attempts to rescue my system I saw information about sda1 etc. exactly like the ones in the very first post here.

At the end of today just about to give up I made a google search for help and found this guide: 
[URL="http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.htm"]http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.htm
[/URL]

After reading that I suddently realised what the 'little house' button is and that it must have been activated. Instead of pushing power on I hit this button again and Ubuntu booted as if nothing had ever been wrong. The above looks like a great guide for those who wants to dual boot and still have the Media Direct thing working.. I have also seen posts in here mentioning the guide, but haven't tried it myself.

I found this post here after fixing the problem by accident, and I also found these - might be useful to others with this problem:[URL="http://ubuntuforums.org/showthread.php?t=472217"]
http://ubuntuforums.org/showthread.php?t=472217[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=606345"]http://ubuntuforums.org/showthread.php?t=606345
[/URL]

Thanks for the forum and all the great tips.. I'm learning new stuff every day!

---

