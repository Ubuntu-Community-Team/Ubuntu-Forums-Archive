---
title: "Boot repair after win8 refresh destroyed GRUB2 on Asus UX31A"
date: 2013-01-27
forum: Installation &amp; Upgrades
---

### Post by chrisbarton on 2013-01-27
Dear All

History: I successfully installed xubuntu 12.10 onto my Asus UX31A, which has win8 pre-installed, UEFI, 256GB SSD, GPT. I did this by disabling Secure Boot & enabling CSM in UEFI settings. GRUB 2 installed and I ran the ubuntu boot repair tool (from usb) to correct the known bug which caused win8 not to load.

Later within win8, an MS update led to a major failure of my win8 system, requiring to do a system refresh (by pushing F8) using recovery partitions. This then led to win8 overwriting GRUB2 with its own MBR and I can now no longer access my xubuntu 12.10. (damn you MS!!)

I do not know the source of the win8 error, but fear GRUB2 perhaps clashed with an MS update for its own bootloader. (of course, it may have been a win8 software compatibility issue.)

I now wish to regain access to my xubuntu. Yes, I can rerun the ubuntu boot repair tool and do the recommended repair but this will undoubtedly reinstate GRUB2. BUT, for warranty reasons, I'd prefer to retain the windows MBR whilst also reinstalling GRUB2.

So, can someone please give a step-by-step guide for a n00b like me on using the _ubuntu boot repair tool's advanced settings_ to purge grub2 (if necessary), reinstall grub2 and then restore the MBR. I am simply afraid to **** the whole thing up and find no guidance on this stuff anywhere!

Thanks in advance!

Christopher

---

### Post by oldfred on 2013-01-27
CSM is legacy or BIOS boot mode which you cannot dual boot with UEFI. Boot-Repair perhaps converted your BIOS install to UEFI by uninstalling grub-pc and installing grub-efi.

Did Windows totally overwrite the efi partition?

Run this so we can see details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by chrisbarton on 2013-01-29
Hi Oldfred - thanks - I'll look into it. I can't comment on the CSM bit but this might have been an issue somewhere, not sure. I had read somewhere that this should be enabled.

For the rest, I simply followed the advice I found here to install xubuntu:
[http://gingerbreaddesign.co.uk/todd/2012/11/09/ubuntu-windows-8-dual-boot-on-asus-ux31a/](http://gingerbreaddesign.co.uk/todd/2012/11/09/ubuntu-windows-8-dual-boot-on-asus-ux31a/)

I've not yet had a chance to run anything you suggested but just thought to make things clear in the meantime...
During  my initial installation of xubuntu 12.10, GRUB 2 installed fine (taking  over the original win 8 bootloader) and windows 8 was able to run  without errors for quite some time, booting up from GRUB 2 (after having  initially run the ubuntu boot repair tool using the recommended  repair). 

It was about a month or so later when the automatic MS  updates for win 8 installed that things went wrong. I do not believe  GRUB 2 to have been the source of the problem. Like I said above, it  could have been a software compatibility issue.

In an ideal  world, I would be happy to reinstall xubuntu onto a dedicated logical  partition (with various sub-partitions like /boot, /, /home), but I've  struggled to find info on doing this on a win 8 preinstalled UEFI  machine with SSD GPT. I have very new hardware and most info relates to  normal pcs without UEFI, with win 7, standard HDD etc, ....so the  situation is never quite matching my scenario.

In any case, I'm  now wary that I will mess things up with "maybe solutions" to the point  that I void my warranty or brick my machine. I simply do not fully  understand this new technology. This is why I'd ideally prefer to have  the original windows bootloader reinstated even though I'd happily have  GRUB 2. 

I tried solving things with EasyBCD too, and this  bizarely showed two entries for ubuntu relating to EFI (I can give this  later, if it helps). I guess these are the leftover pieces after win 8  reinstated its bootloader. This indicates that not everything was  written over, but enough to kill access to xubuntu after doing the win 8  refresh (= reinstall but keeping your MS apps --- all other software  installed from the internet, not the MS Store, is wiped. Your documents  are saved.).

If I went for a full reinstall of xubuntu, then I'd  like to know exactly what to do during installation to retain the  original MBR whilst still having a bootable xubuntu.

I just wish  windows could be smart enough to see or at least respect the fact that  access to other OSes should be retained rather than killing it. Such  arrogance from MS.

Thanks for your help :-)

Christopher

---

### Post by oldfred on 2013-01-29
The instructions in your link installs in UEFI mode not legacy/BIOS/CSM mode.

You usually have to turn secure boot off to install, but Ubuntu is one of the few with the Microsoft key and should boot with secure boot on.
You also need to turn fast boot off.

With UEFI and gpt partitioning there is no 4 primary partition limit. It now is 128. :)
So no extended nor logical partitions.

Normal desktops do not need separate /boot or other system partitions. Some users like a separate /home to make it easier to reinstall. And if just starting that is a good choice. But if dual booting a shared NTFS data partition is better and with Windows 8 that shared data is even more important.

I would always backup efi partition separately. Once you get Windows updated, resized, housecleand, you should make a full backup.
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

We are finding some UEFI systems will only boot the Windows boot file, so the work around was to rename the Windows file and rename the grub shim file (which has Microsoft secure boot) to boot. Then grub chain loads to the backup Microsoft file. Perhaps the Microsoft update replaced the Microsoft efi file?
The entire purpose of UEFI was to allow multibooting, so if your computer vendor only enables Windows boot it is not the intent of UEFI.

---

### Post by LostFarmer on 2013-01-29
It if very possible when you did a Win 8 restore the linux partitions are now gone.  You need to look at the hdd partition to see.  From MS 8 use 'disk management' or best from a live cd use 'gparted' or some other.

After it is known if linux is/not on the hdd, other advice can then be given.  We need to know its current state.

On my new asus , from a live linux I made a copy using 'dd' of the GPT and sda1 (EFI) partition.  I did have to re-install both backup's for a user made mess up.

>  Such  arrogance from MS.  Linux has its own arrogance in relocating the start of the 'extended partition' in a MBR disk and trashing grub if it is installed there.

---

### Post by chrisbarton on 2013-01-29
@Oldfred

Again, thanks for the tips/links. If I remember, I think Secure Boot had to be disabled to enable the usb to boot. Perhaps later switching Secure Boot back on might indeed work after installation. I did not try installation with Secure Boot on, but if it is possible then how come the advice I found required it to be disabled? Also, what to do with CSM now - on or off?  (By the way, I tried running the xubuntu live usb and this could not boot unless I had CSM enabled.)

@Lostfarmer

Thanks - I had already checked this and can confirm my linux partition is still there. This is because I did a refresh as opposed to a full reinstall. The latter would indeed have wiped everything on the disk, starting from scratch. I'll post the partitions later when I'm back home. 

Cheers, C.

---

### Post by chrisbarton on 2013-01-29
BOOT-INFO

[http://paste.ubuntu.com/1586959/](http://paste.ubuntu.com/1586959/)


PARTITIONS (as seen from Windows Disk Management):

Disk 0 Basic 238.35 GB Online

EFI 300MB
Recovery Partition 600MB
OS ( C: ) 102.54 GB NTFS
Xubuntu ( E: ) 97.04GB
Primary Partition 3.89GB (I think this is swap for xubuntu)
DATA ( D: ) 10GB NTFS
OEM Partition 4GB
Recovery Partition 20GB



EasyBCD 2.2 gives the following info:

[I]There are a total of 3 entries listed in the bootloader.

Default: Windows 8
Timeout: 30 seconds
EasyBCD Boot Device: C:\

Entry #1
Name: ubuntu
BCD ID: {7e121d07-6282-11e2-8f7e-806e6f6e6963}
Device: \Device\HarddiskVolume1
Bootloader Path: \EFI\ubuntu\grubx64.efi

Entry #2
Name: ubuntu
BCD ID: {7e121d08-6282-11e2-8f7e-806e6f6e6963}
Device: \Device\HarddiskVolume1
Bootloader Path: EFI\Ubuntu\grubx64.efi

Entry #3
Name: Windows 8
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.efi[/I]

---

### Post by oldfred on 2013-01-29
I do not know about EasyBCD. They also recently updated it to work with UEFI as it did not. But with UEFI I really do not see any reason for it, but then we are a Linux site and like grub2.

CSM is legacy and you seem to be booting Boot-Repair in legacy mode.
> The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.

---

### Post by chrisbarton on 2013-01-29
Regarding CSM, here is what I had written:

> **chrisbarton said:**
> 
I tried running the xubuntu live usb and this could not boot unless I had CSM enabled.


So, although I had wanted to run the live usb with CSM disabled, it didn't want to work. It came up with an error. Where am I going wrong with this? 

Do I need to recreate the live usb whilst within windows perhaps with Secure Boot enabled and CSM disabled to be sure it identifies those things?

I also don't care too much for EasyBCD and only added the details for your info. I am more than happy to use the ubuntu boot repair tool, and, as I had stated in my original question, I was hoping to get a step-by-step guide (perhaps using its advanced settings) to re-establish access to xubuntu but with the MBR restored, purely for warranty reasons.

How shall I proceed exactly?

Thanks in advance

Christopher

---

### Post by oldfred on 2013-01-29
Have you also turned off Intel SRT?

Intel is the standard so brand of computer does not matter.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it. 
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

    

---

### Post by chrisbarton on 2013-02-03
Hi Oldfred

Thanks for the links, which I've spent time studying.

I am pleased to say, however, that I've not needed to do anything whatsoever on Intel SRT settings and have, by some accident, been able to boot back into my xubuntu system! :-)

What I did was to first go into windows 8 and change the power settings to turn off "fast start". I am sure I already did this from the boot settings (within the UEFI settings) by pushing "esc" quickly on start up (on other pcs, this will different, say F12, F2, etc). However, I believe windows 8 resets this to being back on which is why its worth switching it off from within windows itself.

See: [http://www.addictivetips.com/windows-tips/what-is-fast-startup-windows-8-disable-it/](http://www.addictivetips.com/windows-tips/what-is-fast-startup-windows-8-disable-it/)

After following the instructions on the above link, restart the pc, and you will see the Windows Boot Manager. This does not show ubuntu listed, and at first, I thought only had access to windows 8 and that grub 2 had been destroyed by the "refresh" of windows 8 after it had become corrupted.

However, pressing "esc" with the windows boot manager on screen (so, not to be confused with pressing "esc" at start up, which gives access to UEFI settings), gave me access to grub 2. From there I had access to my xubuntu.

For the record, I did this with CSM disabled & Secure Boot disabled. Again, I made no changes to Intel RST.

I therefore did not need to run ubuntu boot repair tool whatsoever yet have regained access to xubuntu which I thought I had lost after the windows 8 refresh.

The next step for me is to find out how to edit the windows boot manager to get xubuntu listed (but this an MS not ubuntu issue). In any case, I happy to have my beloved xubuntu back!

Here is my boot-info file for your information: [http://paste.ubuntu.com/1604337/](http://paste.ubuntu.com/1604337/)

Kind regards

Christopher

p.s. I will now try to confirm if booting from live usb in UEFI mode will work as it should. Other than that, I guess my situation is solved. Thanks again for your support Oldfred.

---

### Post by oldfred on 2013-02-03
If from UEFI (not Windows) you set ubuntu as boot device you should get grub menu and the option to boot Windows. Boot-Repair has added a correct chain load entry as the os-prober has a bug and still creates MBR type entries that will not work with efi.

You may be able to use something like EasyBCD to modify Windows boot to multiboot, but that is another third party boot loader and is not required if you boot with grub.

---

