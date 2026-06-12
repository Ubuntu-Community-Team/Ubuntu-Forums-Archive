---
title: "Preparing to Install 15.04 Onto New Lenovo Notbook Advice Please"
date: 2015-10-09
forum: Installation &amp; Upgrades
---

### Post by LaughingHorse on 2015-10-09
Hi!

I'm preparing to install Ubuntu side by side with Windows onto a Lenovo notebook.

Windows is just there for the Myopic Windows companies, so it will get extremely low use. Primarily for updating certain hardware and devices (like my Olympus camera that does not support Ubuntu... Olympus I'm talkin to you :) )

The Notebook has:
[LIST]
[*]5th Generation Intel Core i5-5200U Processor (2.20GHz 1600MHz 3MB) 
[*]Windows 10 Home 64 
[*]Intel® HD Graphics 5500 
[*]8.0GB PC3-12800 DDR3L 1600 MHz 
[*]500GB 5400 RPM 
[/LIST]

How would you recommend I partition the HDD?

Is there anything else I should be aware of?

Additionally I would like to install CLAM AV. The last time I installed CLAM, it kept running every 5 minutes and then building this massive database that left me no room on the HDD. Any tips on installing CLAM and getting it to play nice as well?

Thanks in advance!

---

### Post by ajgreeny on 2015-10-09
You may find that 15.10 which is due for release very soon is even better on the graphics hardware than 15.04, though I am not certain about that.

Perhaps worth a try as live OS of both.

---

### Post by LaughingHorse on 2015-10-09
That one will be updated to 15.10 when it's released. But for now I need to have them running side by side.

---

### Post by LaughingHorse on 2015-10-09
So should I just let eh installation disk determine the settings then?

---

### Post by Geoffrey_Arndt on 2015-10-09
So, how familiar are you with:

>  shrinking the Windows partition and creating space for Ubuntu?
>  Are you good on partitioning and using apps like gparted? 
>  the latest Ubuntu UEFI install procedures?  (like turning off fast boot and windows hibernation), 
>  familiar with the uefi/firmware interface (how to do one-time bootups, change drive order, etc.)
>  do you have the disk rescue CD (yannubuntu's) and or the Windows rescue dvd?

Just a few things to consider (if not already considered and handled).

Re pre-partioning, might be helpful to see a screenshot (using gparted) of current partitioning scheme.

---

### Post by LaughingHorse on 2015-10-12
Here is a Gparted image of the disc

In answer to your questions:
**Are you good on partitioning and using apps like gparted?**
I'm competent. I don't know if you would call it good.

[B]shrinking the Windows partition and creating space for Ubuntu
[/B]Never did that before. I have done it with Ubuntu before however. SO any tips you can give me will be appreciaed.

**the latest Ubuntu UEFI install procedures?  (like turning off fast boot and windows hibernation)**
Not familiar. THough as I said previously, I have installed Ubuntu 14.04 and 15.04 THough as I said previously on hard drives. Just never partitioned a windows drive.

**familiar with the uefi/firmware interface (how to do one-time bootups, change drive order, etc.)**
I know how to change drive order.

Thanks in advance for help and guidance :)

---

### Post by Dennis N on 2015-10-12
The only place to make room for Ubuntu is to shrink /sda3. The consensus advice is that shrinking that Windows partition should be done from Windows itself using its disk management tools - don't use Ubuntu to do that.

---

### Post by LaughingHorse on 2015-10-12
I was thinking of shrinking the widows portion to 150 gig as it is almost never used, and leaving the rest for Ubuntu.

Once is is shrunk, is there anything else I should be aware of?

Any tips on partitioning? I know the boot mode on this computer is UEFI.

---

### Post by ubfan1 on 2015-10-12
After shrinking the partition, run chkdsk on it a few times.
GPT disk partitioning is simpler in a way since there is not a 4 primary partition limit.
8G swap (may be overkill, depends upon usage), one or two 20-50G partitions for root (always like to try the next version without having to jump off the upgrade cliff), and the rest a (shared by all the roots) data partition (some call it /home, but with different roots, running different releases, you are better off with a release specific /home/user, and a shared data location).

---

### Post by oldfred on 2015-10-13
Some examples:
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

 But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/](http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/)
Something Else install, but prefer larger / of 20 or 25GB. Not showing Windows
[http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/](http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/)

Lots of links in the link in my signature.

---

### Post by LaughingHorse on 2015-10-13
Hi OldFred!

I read the article [http://www.dedoimedo.com/computers/d...-8-ubuntu.html](http://www.dedoimedo.com/computers/d...-8-ubuntu.html)

it was very helpful to my understanding and procedures. Thank You!

I'm not quite sure by what you mean

> I suggest using Windows to shrink Windows

Also, I'm wondering based on the screenshot of the HDD on my computer, if I should just Resize sda3 down to 170GiB as I really don't use windows, and not mess with trying to get extra space form any of the other partitions.

What do you think. Just do the min, or a bit more?

When it comes time to install, will do I need to direct the bootloader to /dev/sda or will it automatically do that?

Thanks in advance!

---

### Post by Dennis N on 2015-10-13
You need to boot into Windows, and use their disk management utility to shrink the partition. As to size, that is up to you. With UEFI and the Ubuntu ubiquity installer, you can't control over where the bootloader is installed - it's automatically to the first EFI system partition that is found starting on the first sata disk even if you specify otherwise in the option box, so in your case it will go to sda1. (So, I assume if we had the EFI system partition at sda3 instead, it would find and use that.)

Good luck.

---

### Post by LaughingHorse on 2015-10-13
Thank You. Before doing any resizing I am running Windows "Optimization" utility on the whole drive. Then I will shrink using the Windows Disk Manager. Optimization had never been run apparently. I'm kind of surprised they did not run it after installing windows, and the Lenovo software.

---

### Post by Geoffrey_Arndt on 2015-10-13
All good tips, you're on the right track.   After shrinnking, be sure to reboot into Windows at least once, preferably twice.    After 2nd successful windows bootup, this is a good time to turn off (disable) hibernation and/or fast boot.   I've never had a uefi win machine, but I've read here and elsewhere the terminology is slightly different depending on pc brand, win 7, 8 or 10, etc.   On some Win PC's, there are two different places to disable hibernation (control center>power settings, and in the uefi setup screens).

So the free space will be unallocated (not formatted & assigned).   You can use gparted to format to ext4 . . . but reformat will usually be required a second time during the actual Ubuntu install.    Good luck.

---

### Post by LaughingHorse on 2015-10-13
After shrinking WIndows, I created the following partition scheme.
Any suggestions before I do the install?

Also, out of curiosity, why does the fast boot/hibernation need to be turned off?

---

### Post by oldfred on 2015-10-13
Partitions look fine.


Bunch of links on topic of fast start up/hibernation.
 WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast startup
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)
Fast startup is hidden.
If issues you may need these?
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavailable, make sure fast startup is unchecked 
powercfg /h off

---

### Post by LaughingHorse on 2015-10-14
Ha! Those links were very enlightening. No comment on why i think M$ is doing this.

I'm about to install, and I want to make sure this looks right.

So I took a screen shot of the installation type before installing. So I have time to change things before the install.

Does this look right?

---

### Post by oldfred on 2015-10-14
You have to select your ext4 partitions and use change to choose / & /home if that is what you want. 
It show sda which is correct. It will then auto find ESP - efi system partition. And since you have swap it will auto find that also.

Seems like different models of Lenovo may have different issues. Not sure if any of these will apply to you once you reboot.
 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)
Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)

---

### Post by Geoffrey_Arndt on 2015-10-14
My personal preference is just to have two linux partitions (/) and Swap.    It keeps things _simpler and more identifiable_ during install.    The advantage to a separate /home partition is saved settings, etc.   It normally takes less than an hour for me to "tweak" a new install or upgrade and by doing so, it refreshes my memory of what's what and how to do the tweaks in the first place.    But, that's just my preference.    Otherwise your system looks ready for Ubuntu . . . . best o'luck!

---

### Post by LaughingHorse on 2015-10-14
I did the install. And everything is working properly. Even no problems with Grub!

I will leave this thread open for one more day in case there are any questions regarding any tech specs on the Lenovo, or anything else.

My initial process was to use Windows Disk Manager to shrink the partition I was going to install Ubuntu on. (as advised by some very smart and helpful people on this thread [THANKS for the Head's up!!!])

Then after the disk was shrunk, I optimized the disk (using Windows utilities in Disk Manager)
After Optimization I logged out, logged in again and tested windows.
Then I followed the instructions in link OldFred Gave
[http://www.kapilarya.com/enable-or-disable-hybrid-boot](http://www.kapilarya.com/enable-or-disable-hybrid-boot)

And disabled "Fast Startup"

Then I used Gparted and Partitioned the disk.
Finally I did the install.

---

### Post by oldfred on 2015-10-14
Glad that worked.

If you have issues with something other than installing, best to start new thread with title relating to issue.

---

### Post by LaughingHorse on 2015-10-15
I will. And OldFred, I could not have done it without your help... well, not as easily anyway :)

I just figured if anyone had any question about what I did or did not do, or needed any clarification.

---

### Post by LaughingHorse on 2015-10-15
Thank you to the people who responded with advice: ajgreeny, ubfan1, and especially Dennis N, Geoffrey_Arndt, & OldFred

---

