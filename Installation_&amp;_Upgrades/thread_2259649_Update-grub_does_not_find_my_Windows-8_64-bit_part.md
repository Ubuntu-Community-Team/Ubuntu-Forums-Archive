---
title: "Update-grub does not find my Windows-8 64-bit partition"
date: 2015-01-06
forum: Installation &amp; Upgrades
---

### Post by aqk on 2015-01-06
Machine: Older (2010) i386 system with 8GB and **PRE-uEFI BIOS** Hey- so the BIOS is from 2010!  Is it THAT old?
HD0:  
 sda1 has  Ubuntu 14.04 x64  system.
 sda2 is linux swap
 sda3 has Windows 8 x64 system.
 sda4,5 should not interest you... Nor should HD1. 

When I do a sudo update-grub, it does not find the Windows on my sda3. But it used to (6 months ago)

I have done several sudo boot-repair incantations, as well as complete removal and re-install of these things,and
the boot-repair hangs at the end of "found initrd image:...  (oldest one here)   So I have to kill it.  -  Ctrl-X
 
The next invocation of sudo update-grub   gives  -
[COLOR="#0000CD"]Found initrd image: /boot/initrd.img....etc etc.... oldest image...
rmdir: failed to remove &#8216;/var/lib/os-prober/mount&#8217;: Device or resource busy
rmdir: failed to remove &#8216;/var/lib/os-prober/mount&#8217;: Device or resource busy
^Z
[2]+  Stopped                 sudo update-grub[/COLOR] 

And the Windows sda3 is not found. Of course the latest Grub-customizer will not find it either.   
I have ways of screwing around with Grub (ie dumping it and finding another boot system) to eventually get the Windows back, (and sometimes resulting in the EXT4 partition not being found instead!)
Or copying the Win section from an older cfg bkup into the grub.cfg...
but-  **HEY!  DO NOT PLAY WITH /boot/grub/grub.cfg - upon pain of death! ** OK, then ..
What is the problem with grub?

 My PC system is SIMPLE:  
   sda1 has Ubuntu 14.04 on it.
   sda3 has Windows-8 on it.  With a BOOT flag.

  And please don't advise me to tell Windows to not do "Advanced Boot".  It does not know what this is. Presumably because my BIOS does not support EFI.
      
 Do I have to buy a new Mainboard whose BIOS supports uEFI to fix this?
Why do I have this problem now?
My Ubuntu (64-bit) and my Windows-8( 64-bit) have existed peacefully together for the last two or three years! And I have done update-grub several times with the present system.

What happened with GRUB recently? How do I fix this?

---

### Post by fantab on 2015-01-06
Post the *Bootinfo Summary* **url** which Boot-Repair tool creates.
Try to avoid grub-customizer if you can.

---

### Post by oldfred on 2015-01-06
The Linux NTFS driver will not mount partitions with hibernated nor chkdsk flags set to prevent damage to NTFS file system.
Make sure Windows is not hibernated, and now with Windows 8 it always is hibernated with fast boot.

 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 

      
 WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by aqk on 2015-01-06
> **oldfred said:**
> The Linux NTFS driver will not mount partitions with hibernated nor chkdsk flags set to prevent damage to NTFS file system.
Make sure Windows is not hibernated, and now with Windows 8 it always is hibernated with fast boot.


Ahhhh... possibly!  I had turned off the fast boot option a while back, as Ubuntu could not access my Win8 NTFS partitions, so I don't think it has hibernated naturally.
But I may have pressed the "power" button on my keyboard as a last step at night. I notice this power button causes Windows to hibernate.

Now-  all I have to do is figure out how to get back into Windows again from Grub, and make sure it is CLOSED Completely!
(sigh... here goes another repair-grub and deletion of uEFI stuff again...)

 Thanx!

---

### Post by oldfred on 2015-01-07
I am not sure I have seen any way from grub to get into a hibernated Windows.

Often just reinstall a Windows boot loader temporarily with either Boot-Repair or your Windows repair flash drive and then from Windows shut down correctly. 

Then with Boot-Repair or manually reinstall grub to MBR.

---

### Post by ubfan1 on 2015-01-07
There is an option on the ntfs-3g mount, remove_hiberfile, see [http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by aqk on 2015-01-07
> **ubfan1 said:**
> There is an option on the ntfs-3g mount, remove_hiberfile, see [http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)
 OK will look at this.
....
> **oldfred said:**
>  
The Linux NTFS driver will not mount partitions with hibernated nor chkdsk flags set to prevent damage to NTFS file system.  
 
Old Fred? Hey.. I am older than you...

I checked Windows **"fastboot"** and yes I had previously set it to **"off"** AND had completely shut Win8 down.

I managed to start WIn8 by copying an old saved  Win8 Grub "paragraph" into the grub.cfg.  Kinda clumsy, but it worked, after I went into Grub's Ubuntu list of "older kernels" and added this. LOL
When I booted, yep- there it was! My Win8 paragraph! It is now classified by Grub2 as an old Ubuntu Kernel. And it boots OK.  Linus T.  must be happy!

Anyhow, I eventually went back and booted Ubuntu and did a apt-get update..  Hmmm...  Accordinfg to SOFTWARE-UPDATER, it seems **someone has recently been frantically working on Boot-repair!** Right? Did I precipitate this?
So I installed today's boot-repar, and ran it.  
It got stuck on the **[COLOR="#0000FF"]"Scanning Sytems (OS-Prober) This may require several minutes"[/COLOR]**   LOL! I left it for two hours while I watched TV (Charlie Hebdo stuff) , but then had to kill it.
Seems more work is required on boot-repair., I guess.

If the boot repair guy(s) read this,  lemme know!** I'll be glad to help you! REALLY!** Just tell me what to do!
(sorry- late at night, and all this wine has made me giddy!)

But at least I can boot my Win8 now as an Ubuntu "old kernel"  ... Until I figure out how to properly edit  the "NEVER TOUCH" **grub.cfg,** "upon pain of death"   
LOL!  I can live with this weird Grub for now! 
Until I REALLY decide to permanently change grub2's Grub.cfg and say to hell with all these weird editing programs, and the 10, 20 30, 40 associated files...! BEWARE.

---

### Post by oldfred on 2015-01-08
I turn off os-prober and only add my other installs with 40_custom.

Years ago - From Ranch hand
 You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09, 25, 40)


 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

Yann, I think, still is the only developer on Boot-Repair. Review bugs on continuous scanning & maybe file a new one. My old system did take a while, like 5 minutes as I had many partitions with many test installs to find. But if it hangs on the scan, there is some partition with issues that is is not bypassing correctly. It does do that as I see many reports with NTFS not mounting or Boot-Repair running fsck on a Linux partition.

 [https://bugs.launchpad.net/boot-repair](https://bugs.launchpad.net/boot-repair)

Just looked and that is a bug already. Sign up for lauchpad and add that you have same issue. Current bug says incomplete, so he may need more info on why it is hanging up. Some suggestions on avoiding issue also in bug thread.
[https://bugs.launchpad.net/boot-repair/+bug/1064323](https://bugs.launchpad.net/boot-repair/+bug/1064323)

Boot-Repair is primarily just running many Linux commands, so you may need to run that command and see why it hangs. But do not know details other than most of Summary report is familiar output from various commands like blkid, fdisk, parted and others. Some is reading certain bytes and converting to readable info.

---

