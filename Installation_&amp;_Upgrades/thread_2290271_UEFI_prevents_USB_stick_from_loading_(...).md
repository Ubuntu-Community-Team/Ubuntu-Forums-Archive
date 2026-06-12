---
title: "UEFI prevents USB stick from loading (...?)"
date: 2015-08-11
forum: Installation &amp; Upgrades
---

### Post by david421 on 2015-08-11
Ladies and gentlemen, I've tried everything.  I'm a relative noob with Linux, so please bear with me.

I'm attempting to set up a dual boot with Windows 7 on a relatively new system.  Windows loads fine, which confirms that the hardware is in order and assembled correctly.  My working hypothesis right now is that my UEFI-based motherboard is causing issues.

**System:**
*Mobo:*   Gigabyte Z97-HD3 rev2.0 (recently flashed to latest firmware vF8)
*CPU:*     i7-4790k 4.0GHz
*RAM:*    16GB
*Gfx:*      NVidia GTX 980
*SATA0:*  500GB ssd (currently unpartitioned / departitioned)
*SATA1:*  240GB ssd (currently disconnected for troubleshooting purposes)
*SATA2:*  4TB hdd (currently disconnected for troubleshooting purposes)
*SATA3:*  4TB hdd (currently disconnected for troubleshooting purposes)
*SATA4:*  {empty / unoccupied}
*SATA5:*  Optical drive

**History: (I have no idea what is useful info and what is not, but this is my best attempt to provide synopsis)**

*First:*     System self-built with all new components approx. early April 2015.  Only recycled component was optical drive and 240GB ssd (SATA1 above).  System worked fine with Windows 7 prior to purchase of 500GB ssd (SATA0 above).  Main drive was 240GB ssd (SATA1 above) alongside 500gGB hdd (removed) and both 4TB drives (SATA2/3, above) were in use, independently partitioned (E:\ and F:\, respectively) for synching with various cloud storage (Dropbox, OneDrive, and others).

*Second:* Purchased SATA0 late July 2015, moved SATA1 to current position, removing other hdd not listed above.  Left both 4TB drives alone, NTFS clean-formatted x2.  Successfully upgraded to Windows 10, experimented for ~2 hours, didn't like it.  Formatted and installed Windows 7 instead to occupy entire SATA0.  Intention was to install Ubuntu v15.04 Vivid Vervet on entire SATA1 with WUBI installer on USB.  (Note -- later steps involve switching to a different USB creator.)

Error at this stage: Ubuntu installer could not identify any active partitions on any drive.  I chose to halt my progress.

***[I]HANDHELD CELL PHONE VIDEO SERIES OF THIS ERROR IS AVAILABLE!!!***  Link to dropbox folder is: [https://www.dropbox.com/sh/308uti0843fp7da/AADErdVl3to1rJXxiHfqCuzUa?dl=0](https://www.dropbox.com/sh/308uti0843fp7da/AADErdVl3to1rJXxiHfqCuzUa?dl=0)  Note several video segments (I attempted to break the video sequence every 30-40 seconds to keep individual segment sizes small.)  Files are numbered in order.  Text file contains annotations.  Note that some 30-second segments are omitted for being uneventful, and these breaks are annotated within the .txt file.  Unnumbered video segment at the end relates to later step and is not annotated.

Third:[/I]  I switched to Windows 7 to verify function, and discovered that somehow, the Windows bootloader partition (~100MB, silently created by Windows setup) was placed on SATA1.  I anticipated that this would cause issues with GRUB.  Perhaps too hastily, I departitioned all four drives.  When attempting to reinstall Windows 7 (after removing Windows 10) in anticipation of dual boot with Ubuntu, successfully placed Windows boot partition on SATA0.

Error at this stage:  SATA2 was somehow "bifurcated".  I have no other idea how to describe condition; total drive space available added to 4TB (to the last MB when compared to space assessment of twin SATA3) but was forcibly restricted to first partition of ~2.3GB, second partition of ~1.6GB.  I could sub-partition and then delete-and-re-partition within those bifurcated halves, but could not extend any one partition segment across whatever boundary had been placed between the two segments, and repeatedly attempted to do so from each direction (first extending from the 2.3GB side, then from the 1.6GB side).  Various boot experiments verified that the both drives performed comparably to each other in circuit testing, and were purchased as twins, so as to ascertain possible media failure.  Read-write / partition-format (FAT32, NTFS and ext4) / connect-disconnect tests all suggested that the drives were working fine, and always registered on BIOS when properly connected and powered.  Purchased an external USB enclosure for isolation tests (and to verify that I'd identified the correct drive of the two, and obtain serial number info, for possible RMA.)  Issue spontaneously resolved during or subsequent to the relocation of these drives to an external enclosure.  I repeated all abovementioned troubleshooting steps, hoping to reveal hardware failure.  Drives are both working fine, each with a unified space allocation.

*Fourth:*  Abovementioned troubleshooting resulted in all drives departitioned again.  Partitioned SATA0 to accommodate 350GB for Windows 7, ~140GB for Ubuntu, ~10GB for Ubuntu swap.  SATA1-4 remained connected and departitioned.  Intent was to prove concept of dual boot, then separately address preference for separate drives (intending to delete and reinstall at least one last time.)  Verified Windows 7 install and proceeded to attempt Ubuntu install.

Error at this stage:  Ubuntu installer hung during boot, never reaching drive select stage.  This was replicable.  Error message suggested that the installer hung when attempting to load a generic graphics driver.

*Fifth:*     Hypothesis from previous error was poor access to a useful graphics driver.  My video card is rather high-end, and the FOSS driver might not be up to snuff quite yet.  Switched from WUBI to LiLi USB Creator (run in Windows 7 on unaffected laptop).  Switched to Lubuntu for troubleshooting purposes with its lighter weight (with every intention to return to Ubuntu for final install.)  Used three different USB sticks to assess possibility of USB media failure.

Error at this stage:  "Lubuntu fail" (unnumbered video at the end of the series in the link above).  Installed to the error in that video, then ran live from USB without uninstalling.  From USB live desktop, attempted to download and install proprietary graphics drivers.  Did ultimately manage to get to a working Lubuntu desktop and installed proprietary graphics drivers, though I don't exactly recall what steps I took to do so, nor -do I understand why those steps worked.  I booted into the Ubuntu installer from the USB, it detected the underlying Lubuntu install, and I thought that solved my problem.

*Sixth:*    At this point, the mistake that I made wasn't perhaps the biggest, but it is the one that is the most frustrating in hindsight.  I thought I'd solved the problem -- I could successfully boot into Windows 7 or to Lubuntu through the Grub loader, and all was well.  One remaining issue was that Lubuntu was reading as a 32-bit instance, and I specifically and explicitly need 64-bit for my specific project.  If I cannot run 64-bit Linux, I have exactly zero incentive to run any secondary OS beyond Windows.  The next step was to remove Lubuntu, install Ubuntu with the graphics driver in hand (I anticipated issues getting it to load with the installation boot loader but resolved to work through that) on the same drive and then revert to my preferred distribution of OSes to each drive, assessing 32/64-bit conflicts on the way.  Here, I simply deleted the Lubuntu partition, thinking that my Grub loader would remain unaffected.  *Oye vey*, was I wrong.

Error at this stage:  Here, I did "successfully" install Ubuntu onto a new partition that replaced the one I deleted, above.  However, the first reboot was a fail.  Black screen to a "grub rescue" or something, and no joy from this point.

*Seventh and current:*  All drives are departitioned, and SATA1-4 have been disconnected.  All attempts to load into the Ubuntu installer fail at a hung splash title screen.  No partitions currently exist on SATA0.  I'm pretty sure this is a UEFI problem, and I've seen references to Shim v0.1, but I don't entirely understand this info nor do I know how to use it.  I intend to call my mobo manufacturer tomorrow when they open (they are on California time) but previous calls in connection with the drive bifurcation issue (above) suggest that they're a Windows-centered crowd, so my hopes are small in that regard.

Please help.  :(

---

### Post by kurt18947 on 2015-08-11
I have zero experience with UEFI or modern/high end hardware for that matter. I am also not an IT pro so take this for what it's worth. You mention WUBI near the beginning of your post. WUBI has been deprecated for some time I believe. It may it still work but I think active development stopped some years ago. I also haven't installed Lubuntu in some time so am not familiar with the initial screen. I have had issues installs hanging when loading video drivers on older/weaker hardware like netbooks. A solution that has worked in those cases was to use 'nomodeset'. There's some glare on the bottom of the screen in your first video so i can't see it well but usually there's a message near the bottom of the initial screen to press some key for advanced boot options. Among those options are noacpi and nomodeset, I don't know if nomodeset will help in your case or not but perhaps something to consider.

---

### Post by grahammechanical on 2015-08-11
I have not read your post. It is too long and has too much information that is not relevant. Does it not? So, please start again and be concise. What is the present problem?

Is it that you are trying to install a 32 bit version on a machine that has a 64 bit CPU? It will work because the CPU architecture is backwards compatible with 32 bit operating systems. But we do have a 64 bit version of Ubuntu. The 32bit ISO image is called i386.iso and the 64 bit ISO image is called amd64.iso. Both images will work on Intel and AMD CPUs.

How new is your graphic adapter? The newer the graphic card the newer the version of Ubuntu needed because the newer graphic cards may need newer proprietary video drivers which are not present in earlier versions of Ubuntu. So, you may need to be installing Ubuntu 14.04.3 or Ubuntu 15.04.

My advice when installing is not to tick the box labelled Install third party software. Doing that will install a proprietary video driver. Which is a good thing unless there is some complication. By not ticking that box we can use the open source video driver which in your case is called Nouveau. Which is what the Ubuntu live session uses.

So, if things are fine with a live session but not with the first reboot of an installed Ubuntu then we tend to think proprietary video driver problems. Which is why it is suggested that we try installing a proprietary video driver when in the live session. We can do that.

Once we have a successful installation of Ubuntu we can install the needed audio and video codecs by installing Ubuntu Restricted Extras from the Ubuntu Software Centre and we can experiment with proprietary video drivers by going to System Settings>Software and Updates>Additional Drivers tab.

Oh, I do realise that there is nothing in my post that relates to the title of your thread. So, there is confusion here as to what the problem is.

Regards.

---

### Post by oldfred on 2015-08-11
Windows only boots with BIOS from MBR partitioned drives.
Windows only boots with UEFI from gpt partitioned drives.
How you boot installer is how it installs.
Maximum size of MBR drive is 2.2TiB, you have to use gpt for larger drives.
Ubuntu will boot with either BIOS or UEFI from gpt partitioned drives if correct partitions are on drive.
The boy in the blue shirt lives in the white house.
What color house does the girl in the green dress live?
Damn mixed up puzzles again. I can never solve them :)

If you try to install Windows in BIOS mode on a large drive it makes it MBR, but some tools make an special second partition that only Windows with special drivers can use. Or the use non-standard sector sizes.

Repartition your 4TB drives with gparted or gdisk. Include both a 500MB efi partition and a 2MB bios_grub partition at beginning of drive, even if now you do not plan on installing a system to it. Very difficult to add those when drive has lots of data.
Better with new UEFI system to only use gpt partitioning, but then have to boot Windows in UEFI mode. And then you need to boot Ubuntu in UEFI mode.

Windows 7 default install is BIOS. You have to copy to flash drive and reconfigure so it has the efi boot partition to boot in UEFI mode. UEFI/CSM should give you two options to boot both Windows & Ubuntu, one UEFI: name of flash drive and second is just name of flash drive or BIOS/CSM/Legacy boot.
 Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)

Gigabyte does have some issues.
       Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

What video card? New nVidia Maxwell systems need the newest versions of Ubuntu, either 14.04.3 or 15.04 and newest nVidia drivers.
You may need nomodeset to boot to low quality graphics with nVidia or AMD.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by david421 on 2015-08-11
Awesome!  I'll try all of these suggestions in order once I return home from work!  Thanks folks!

> **kurt18947 said:**
> You mention WUBI near the beginning of your post....

Yes, I do.  However, I also switched to another creator utility later, and noted this.  Thank you for at least validating that I was correct in doing so.

> **kurt18947 said:**
> I have had issues installs hanging when loading video drivers on older/weaker hardware like netbooks. A solution that has worked in those cases was to use 'nomodeset'. There's some glare on the bottom of the screen in your first video so i can't see it well but usually there's a message near the bottom of the initial screen to press some key for advanced boot options. Among those options are noacpi and nomodeset, I don't know if nomodeset will help in your case or not but perhaps something to consider.

Those options were indeed not displayed on the screen, so the glare did not prevent you from seeing those.  Thank you, I see how this info could also have been useful.  See below, however for further progress.  :)

> **grahammechanical said:**
> I have not read your post. It is too long and has too much information that is not relevant. Does it not? So, please start again and be concise. What is the present problem?

Well, thanks for stepping in anyway.  I appreciate it.  Please note, however, that more than one of your clarifying questions are already addressed within my (admittedly verbose) description above.

Note specifically that someone after you brought to my attention the fact that my "bifurcation" issue could very well have corresponded to a Legacy / UEFI conflict, suggesting that my otherwise lengthy descriptions of my hard drive escapades ended up being indeed quite relevant.  Specifically, more relevant than even***I*** would have known beforehand.  My knowledge has been increased, though I am still somewhat ill-equipped to respond to your request to be more concise -- particularly with the belated validation that came from being told that some of my info was useful to an extent that even surprised myself.

> **grahammechanical said:**
> Is it that you are trying to install a 32 bit version on a machine that has a 64 bit CPU?

Absolutely not.  I am aware of 32-bit versus 64-bit hardware / environment / software situations, and was specifically trying to install 64-bit Ubuntu on a 64-bit system.  However, you do deserve to know that you still helped me by mentioning this.  Since I'd begun using multiple USB sticks so as to eliminate the possibility of physical media failures within the USB drives themselves, and since I'd burnt those ISO copies using different utilities (one was WUBI, another was Lili, and there was another utility I used briefly that may have been in the mix) what I thought was that I was using identical ISOs for each thumbdrive.  Upon verifying, I discovered that one of them was 32-bit.  No-the-hell-wonder I was getting such odd results from my troubleshooting!  I have since erased all thumbdrives in use and manually downloaded the 64-bit ISO for Vivid Vervet 64-bit.  I then used Lili to burn and mount said ISO.  Having discovered this error on my own part, I then reset my BIOS to optimized-default parameters, except that I went back in to force it to UEFI-only boot modes.  I also decided to get greedy and reattached all SATA cables to all drives in my system, and proceeded to manually delete all partitions (since I could not be sure if they were MBR or GPT --- see below.)  With the new thumbdrive in hand, I successfully live-booted to Ubuntu on the first attempt.  I tried a few settings without installing, and all appeared in order.  I then backed out, and rebooted to install (I chose not to install directly from the live instance.)  I am hereby typing this reply to you from within a successful hard install!  :D :D :D

> **grahammechanical said:**
> How new is your graphic adapter? The newer the graphic card the newer the version of Ubuntu needed because the newer graphic cards may need newer proprietary video drivers which are not present in earlier versions of Ubuntu. So, you may need to be installing Ubuntu 14.04.3 or Ubuntu 15.04.

This was already my intention.  I cannot be certain, but I suspect that with my multiple USB drives, there may have been some version mismatches.  My intent from the beginning was to install v15.04, and that is what I am running now.

> **grahammechanical said:**
> Once we have a successful installation of Ubuntu we can install the needed audio and video codecs by installing Ubuntu Restricted Extras from the Ubuntu Software Centre and we can experiment with proprietary video drivers by going to System Settings>Software and Updates>Additional Drivers tab.

Thank you, this will be useful to me soon.

> **grahammechanical said:**
>  Oh, I do realise that there is nothing in my post that relates to the title of your thread. So, there is confusion here as to what the problem is.

At the time that I composed my OP above, I was reasonably confident that a UEFI conflict was my exact problem.  My (again, admittedly lengthy and wordy) description of my troubleshooting attempts to far was intended to provide a description as to how I arrived at that hypothesis.  The advice that I have yet had the opportunity to test from you and from others in this thread only strengthens my own assessment that this is, indeed, exactly, a UEFI conflict issue.

Much obliged for your time.

All: Be advised that I am 80% certain that this issue is resolved.  My remaining concern stems from my intention to hopefully install Windows and Ubuntu to separate SSDs, so I want to spend a few hours making sure I've truly addressed the UEFI problem (probably while setting up my dual-boot along the way) before finally marking this thread as resolved.  If I run into dual-boot-specific problems, I would likely ask for help on those in a new thread.

Thanks so far, folks!

---

### Post by david421 on 2015-08-11
> **oldfred said:**
> Windows only boots with BIOS from MBR partitioned drives.
Windows only boots with UEFI from gpt partitioned drives.
How you boot installer is how it installs.
Maximum size of MBR drive is 2.2TiB, you have to use gpt for larger drives.
Ubuntu will boot with either BIOS or UEFI from gpt partitioned drives if correct partitions are on drive.

Wow.  I think this was my breakthrough, here.  I threw my "bifurcation" woes into my description thinking initially that their relevance was with respect to the OTHER troubleshooting steps I'd taken.  It somehow never occurred to me that it could very well have been an earlier symptom of the exact UEFI problem that I suspected I was fighting against.  In any event, the numbers check out.  Thanks!

> **oldfred said:**
> The boy in the blue shirt lives in the white house.
What color house does the girl in the green dress live?
Damn mixed up puzzles again. I can never solve them :)[/QUOTE}

LSAT?  :D

[QUOTE=oldfred;13336730]Repartition your 4TB drives with gparted or gdisk. Include both a 500MB efi partition and a 2MB bios_grub partition at beginning of drive, even if now you do not plan on installing a system to it. Very difficult to add those when drive has lots of data.
Better with new UEFI system to only use gpt partitioning, but then have to boot Windows in UEFI mode. And then you need to boot Ubuntu in UEFI mode.

See above reply.  I currently compose this reply from within a working hard-install of Ubuntu v15.04 64-bit!  :D :D :D  All I did was start over from scratch.  I manually downloaded a 64-bit ISO, erased all USB drives, used Lili to mount the ISO, reconnected all SATA cables, deleted and removed all partitions, and sucessfully live-booted into Ubuntu from the USB on the first attempt.  I chose to reboot and install instead of installing from the live session.

I'll bear your partitioning advice in mind going forward, though I might be drawn in a different direction.  I have yet to install Windows, and I'm aware that I'll prolly have to format and remove Ubuntu first in order for a dual boot to coexist well.  I shall begin that step after composing these thank you's here.

> **oldfred said:**
> What video card? New nVidia Maxwell systems need the newest versions of Ubuntu, either 14.04.3 or 15.04 and newest nVidia drivers.
You may need nomodeset to boot to low quality graphics with nVidia or AMD.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

nVidia GTX 980.  Currently running whatever out-of-the-box driver comes with v15.04, though I may upgrade to proprietary before all is said and done.

Thank you so much!

---

### Post by oldfred on 2015-08-11
You may be installing a new enough versions that video just works. But older versions or if you really want the very newest, it is not in Ubuntu repository. Often kernel, support software & video driver must all be most current version.

If you want the newest driver from nVidia do not download directly from nVidia but use a ppa. If you download from nVidia and install the .run file you have to in effect reinstall with every kernel update before rebooting after a kernel update. 
With a ppa they pre-compile the drive and make it install in the same way Ubuntu repository works. And that is automatically reintegrated into kernel when installed.
 Maxwell 750 - kernel 3.15 or newer required
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://ubuntuforums.org/showthread.php?t=2265505](http://ubuntuforums.org/showthread.php?t=2265505)
Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)

Several ppas discussed, not sure if one better than other as I have not needed them.
      
 The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)
Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[URL="http://ubuntuforums.org/showthread.php?t=2259210"]http://ubuntuforums.org/showthread.php?t=2259210
[/URL]
 PPA for nVidia mamarley pps
[http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945](http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945)
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
All the current drivers xorg-edgers PPA
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)
Oibaf PPA discusion
 [URL="http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1"]http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1

[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=2259210"]
[/URL]

---

