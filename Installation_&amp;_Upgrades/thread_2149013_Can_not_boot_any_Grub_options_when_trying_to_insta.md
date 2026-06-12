---
title: "Can not boot any Grub options when trying to install using EFI."
date: 2013-05-27
forum: Installation &amp; Upgrades
---

### Post by Geezanansa on 2013-05-27
Hi all,

Have recently taken an interest in EFI boot feature on newer systems.  

Had recently posted a similar question here but following the advice in  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) at Chapter 1 Section 6 explains to post questions in this forum which i am doing in the hope to better the chances of getting a solution.  Will post Boot Info Summary soon.

The hardware being used is ga a75 ud4h motherboard which has a Tianocore based firmware using specification EFI 1.1.  The intentions of making this system my first Ubuntu only machine evaporated after being made aware of EFI capabilities or at least Ubuntu's inability to install EFI mode on this hardware.  Windows 8 was slightly easier to get booting and installing EFI mode after creating an USB with both UEFI and BIOS images/files to use as the downloaded ESD only had BIOS image when creating media.  see [http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/is-anyone-else-having-problems-with-uefi-support/a8e39541-941e-498d-9b23-134a9f9ada87](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/is-anyone-else-having-problems-with-uefi-support/a8e39541-941e-498d-9b23-134a9f9ada87)

Using an Ubuntu 12.10 amd64 Desktop dvd on an EFI capable machine have black and white Grub boot options screen running in EFI mode.  Selecting "Try Ubuntu  without installing" or "Install Ubuntu" gives "can not read cd/0" and  "the kernel needs to be loaded first" errors.
 Both .iso and burned disc md5 checksum are good.

Trying latest release of other distros gives similar results. Trying  booting newer and older flavours of Ubuntu gives similar results when  booting EFI mode and trying any of the options available to boot to simply do not work.
Dropping to grub command line and trying 
```
search -f /vmlinuz 
```
 or      
```
search -f /sbin/init
```
 only confirms missing EFI files.  
**Update:** Can not repeat the results using those commands but do get similar output from using      Code:
     
```
ls -l
``` 
 from grub prompt which gives 
[IMG]http://i.imgur.com/FoHVFeo.jpg?1[/IMG]

This is intended to illiustrate the missing file error and hardware info is not accurate.  
A more recent Boot Info Summary can be found at [http://paste.ubuntu.com/5707053/](http://paste.ubuntu.com/5707053/)

How to point grub to usable EFI files in order to boot "Try Ubuntu without installing?" or "Install Ubuntu?" or more simply "How to boot Ubuntu in EFI mode?."

---

### Post by fantab on 2013-05-27
Can you confirm that your CD/DVD drive is working? If its not working then try USB drive.
Do you have a GPT partitioned HDD?
Have your created an EFI partition?
Are you trying to Dual-Boot? If Windows is already there, then does it boot in UEFI?

Let us see the output of [BootInfo Script]("http://bootinfoscript.sourceforge.net/") first and also the screenshot of your partitions.
Do give us your computer hardware specifications.

---

### Post by Geezanansa on 2013-05-27
1) Using USB and DVD media gives same results when booting EFI mode with Ubuntu installer. 
2 & 3) Windows installed EFI mode so drive is using GPT and there is a valid ESP. 
      4) Yes due to Ubuntu's inability to install in EFI mode.  
      5) Windows boots using UEFI.

Have updated q with boot info script and some hardware specs.

---

### Post by fantab on 2013-05-27
Your Windows is in 'Hibernate Mode', shut it down properly then try ubuntu DVD/USB.

[QUOTE=BootInfo Script]
Windows is hibernated, refused to mount. Failed to mount '/dev/sda3': Operation not permitted The NTFS partition is hibernated. Please resume and shutdown Windows properly[/QUOTE]

Even this is an issue: 
> 
Error: Can't have a partition outside the disk!

It means your Partition Table is corrupt. But first get your PC to shutdown properly. And boot Ubuntu disk... if you still have problems then we'll try and fix the partition table.

---

### Post by Geezanansa on 2013-05-27
1) Using USB and DVD media gives same results when booting EFI mode with Ubuntu installer. 
2 & 3) Windows installed EFI mode so drive is using GPT and there is a valid ESP. 
      4) Yes due to Ubuntu's inability to install in EFI mode.  
      5) Windows boots using UEFI.

Have updated q with boot info script and some hardware specs.

---

### Post by Geezanansa on 2013-05-27
Sorry for double post. 



Referring to [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system) - After making sure windows is shutdown rather than restarting as well as Fast Boot disabled from within Windows and then booting with Ubuntu DVD after getting to EFI mode grub screen options still do not boot anything and with same errors.

Windows install has had chkdsk, sfc /scannow and checked for dirty bit.  All appears to be well with windows install. 

Another Boot Info Script was generated after making sure Shutdown was selected before booting to Ubuntu DVD it can be found at[ http://paste.ubuntu.com/5707415]("http://paste.ubuntu.com/5707415")  .


Disconnecting the hard drive and then booting Ubuntu DVD EFI mode and selecting "Try Ubuntu" or "Check disk for defects" throws same errors as listed in question/first post.  Another Boot Info Script was made - [http://paste.ubuntu.com/5707699](http://paste.ubuntu.com/5707699).  Looking at this still gives - "Can't have a partition outside the disk!"
Fantab said > Even this is an issue: 
                                                         Error: Can't have a partition outside the disk!                      

     
 
It means your Partition Table is corrupt.


Referring to [http://paste.ubuntu.com/5707699](http://paste.ubuntu.com/5707699) when drive was disconnected and the other Boot Info Summaries; How could this be if there was no hard drive i.e. no partitions connected.?

---

### Post by Geezanansa on 2013-05-29
After rechecking windows power options disabled hybrid-sleep as part of the process of elimination to stop hibernation mode. All of which is after turning off Fast Start Up and making sure shutdown is used rather than restart as mentioned in earlier post.

After trying to boot 13.04 64bit EFI mode - which it would not do so on this hardware i ran the installer in BIOS mode with machine setup for booting hdd and dvd EFI mode.  (This is the manner how i have been getting tio live session in order to run boot-repair i.e. in BIOS mode.)
I think this could have been contributing to the cause of the "can not have partition outside the disk" errors in boot-info-scripts.
After which running boot-repair from live session resulted in fixing EFI boot files to the appropriate place.

The 13.04 installer when running the "something else" option was very good at keeping me right for making a bios_grub partition and a swap partition.

It would appear the way firmware is hardcoded to handle EFI files was picked up by installer and then boot-repair.

So to recap simply installing Ubuntu BIOS mode to the disk where Windows 8 was EFI installed then running boot-repair's recommended repair fixed EFI boot for Ubuntu which now means that both OS's are booting using EFI mode and both are available to boot at boot time from grub list.

The Boot-Info-Scipt that was generated after running boot-repair's recommended fix now reads like this [http://paste.ubuntu.com/5713889/](http://paste.ubuntu.com/5713889/) and ```
dmesg | grep EFI
``` now returns several lines rather than the one single line after doing the same when booted in BIOS mode all of which confirms booting Ubuntu using EFI.
:P  :guitar: fantabulous fantab :popcorn:soz :lolflag:  :cool:

Mission not quite accomplished yet as part of this systems firmware or EFI management does not provide an EFI shell as this is not part of the EFI specification.  So to help manage this sytem i intend installing rEFInd and an EFI shell following the simple twelve step guide provided by the author of rEFInd and the very useful webpages found at [http://www.rodsbooks.com/](http://www.rodsbooks.com/) all of which this webpage [http://www.rodsbooks.com/gb-hybrid-efi/](http://www.rodsbooks.com/gb-hybrid-efi/) has been a great source of useful and helpful information regarding booting Ubuntu on this type of firmware.

---

### Post by Geezanansa on 2013-05-29
Thought would post a boot-info-script that was generated when actually booting EFI mode which can be found [http://paste.ubuntu.com/5714752/](http://paste.ubuntu.com/5714752/)

---

### Post by Geezanansa on 2013-06-01
Now that i have a dual booting system booting using EFI it would be advantageous to be able to boot installation media EFI mode.  After downloading the latest release of Parted Magic i get same errors as booting Ubuntu installation media so a working answer or an explanation of why the errors are thrown would be appreciated.  i.e. How to boot Ubuntu installer EFI mode?

---

### Post by oldfred on 2013-06-06
Is UEFI/BIOS updated to the newest version from motherboard vendor?

Some systems just do not install in UEFI mode, and the only work around has been to install in BIOS mode and convert after install as you did.

Some need other boot parameters. UEFI writes hardware info differently than BIOS for systems to use. If UEFI is not current or writes something differently then different parameters may be needed than for a BIOS boot.

         [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by Geezanansa on 2013-06-08
Am running the F8c firmware given to me by Gigabyte Global Technical Service which at least means i can now use my wireless keyboard to access BIOS settings predictably... can not confirm any other difference compared to the F8a version.

Have a dual boot system using Windows 8 and Ubuntu 13.04 with grub acting as boot manager for both OS.  

Part of managing an EFI system is registering boot loaders with firmware which in this instance is not achievable by using efibootmgr from Ubuntu or bcdedit from windows but both seem incapable of telling firmware what to do when trying from installed OS and can not boot an Ubuntu live session EFI mode due to the errors given at start of thread. 

Have been using [http://www.rodsbooks.com/gb-hybrid-efi/](http://www.rodsbooks.com/gb-hybrid-efi/) and [http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html) for main guidance.  Have gotten as far as dual booting EFI mode but can not get rEFInd to work as expected when installing but rEFInd does work using the CD.iso.

ttfn

---

### Post by Geezanansa on 2013-08-04
Just a quick update..
rEFInd has been boot manager for Windows and Ubuntu for a while now but Windows is corrupted to the point of being barely usable; which is bootable but very poor performance taking ten minutes plus to boot and log in.  chkdsk taking days to run..  all this is due to trying to set up Android Debug Bridge and mucking about with things i do not understand.  Have managed to flash ICS to an ARM v6 Android phone though!  Shame it can not run Ubuntu Phone...

Any hows,  getting back to the point, this thread is still open as there seems to be no explanation as to why Ubuntu, Fedora, Mint and other distros simply will not install EFI mode.  The nearest to running installer EFI mode is Grub the boot manager loading but Grub the boot loader can not be found.

As briefly mentioned in first post Windows installation media had to be recreated in order for an usable EFI image to be used in order for installer to run EFI mode.
I can not find anything online describing anything of the like for Ubuntu.

As another observation and which is hinted at rodsbooks gigabyte page it may be more than possible the firmware being used can only see Windows EFI images.  Which may also be the reason a default install of rEFInd does not work on this hardware.  As well as contributing to the necessity of running boot-repair to get Ubuntu booting EFI mode after installation.

---

### Post by oldfred on 2013-08-04
Did the new UEFI/BIOS from Gigabyte include an update from UEFI 1.1 to 2+. Ubuntu and Windows are compatible with the newer UEFI. Gigabyte was late in having full UEFI compared to most, but I did see several months ago where they released all new UEFI installs for many motherboards.

I think if you do not have UEFI shell, you can download one from Intel and use it. Intel was one of the creators of the UEFI spec.
 [https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)
EFI/boot/bootx64.efi.efi" ---> Brings up 'EFI shell environment' with command prompt.
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

I think it was only the new systems with Windows pre-installed had UEFIs that were modified to only boot the Windows efi file. Boot-Repair did a work around naming grub's shim to the Windows file name, but no many systems now seem to have that issue. The newest Boot-Repair does not rename automatically, but has it now as an option in Advanced.
Your system has Windows boot file renamed. May be best to undo that.
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

You also have a copy of the original Windows boot file:
      
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

        

The author of rEFIind sometimes posts in askUbuntu, if you have specific issues with that.

---

### Post by Geezanansa on 2013-08-04
Howdy oldfriend

Am actually uncertain to the exact precise EFI version being used as there is very little info from manufacturer. Using efisystab described version as being 1.1 rev 2 (from memory) and rEFInd reports 2.1 being used!

Before buying this board i viewed the webpage for this hardware and there were links regarding a full UEFI gui with loads of funky goodies. After purchasing and feeling let down approached the appropriate people and was told all information is for information only and buy a better board if UEFI is desired!
Regardless; now am using EFI for booting OS's and thanks to rEFInd have a shell environment available which will be useful after getting to learn how to use it!  This hardware does have a fair bit of upgradability SATA 3 = ssd which will be another first for me..  so do still see it as investment.  Just put the experience down to learning... 

Thanks for advice for restoring efibootmgfw.  Have found using bcdboot useful for restoring boot partition data - bcdboot c:\windows /s s: /f UEFI after mounting EFS partition then assigning s as volume label and making sure diskpart sees windows partition as c:

Boot-Repair automatically applied renaming fix for me as well as re-installing grub.efi.

What i am stuck on is working out why installation media that claims to be/is EFI capable is not running installer/try ubuntu or any other grub option after grub boot manager has loaded in EFI mode.

Really would be handy if installation media could be started in same mode as installed OS for say being able to use efibootmgr from live session.

---

### Post by oldfred on 2013-08-04
I thought how you boot install media for both Windows & Ubuntu is how it installs (or repairs). So if you boot flash drive in UEFI mode it should work in UEFI mode. But if you boot in BIOS/CSM/Legacy mode then you have old BIOS mode.

---

### Post by Geezanansa on 2013-08-04
Yes. That is my understanding how it should work also.  This is not the case on this hardware due to "need to load kernel first" error as described.

The penny is dropping - "Boot-Repair will convert a BIOS install to UEFI by uninstalling grub-pc,  and installing grub-efi. It will also rename Windows file if system  only boots Windows and installs grub2's shim that has Microsoft secure  boot key"
A small quote from oldfreds link from his post.

Regardless of bios settings and install mode of Ubuntu; grub has never loaded a kernel EFI mode for me when booting from installation media.  Ubuntu installation media always stops at the black grub options screen with no usable kernels when started in EFI mode.  Which means the only way to boot a live session is legacy mode =  no efibootmgr.

Thought had posted link to the AskUbuntu question i asked in first post but can not see so here it is[ http://askubuntu.com/q/208405/102029]("http://askubuntu.com/q/208405/102029").

---

### Post by oldfred on 2013-08-04
I think some with AMD do have more issues with UEFI for whatever reason.
Do you need added boot parameters either nomodeset or nomodeset and additional boot options?

Another thread posted this as another UEFI/BIOS setting that caused issues.
 Linux kernel enable the IOMMU – input / output memory management unit support - AMD 
[http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html](http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html)
[http://ubuntuforums.org/showpost.php?p=9203674&postcount=5](http://ubuntuforums.org/showpost.php?p=9203674&postcount=5)

---

### Post by Geezanansa on 2013-08-09
Thanks for the links to extra resources oldfred.  Have been trying different options to try and get Ubuntu installer running EFI mode but system hangs and returns the can not read file(vmlinuz) and the kernel needs to be loaded first errors.  Have been overlooking editing kernel parameters and the omnly thing that i can boot to is when "noefi" is used....

As an observation have noticed that when boot repair installs grub-efi the grub_bios partition is left behind which my understanding is that partition would only be used with a legacy install alongside an existing efi install.  So i deleted it using gdisk and still have dual boot system!  Why does boot-repair leave this if it is not needed after installing grub-efi?

Is there a way to boot (FOSS) media EFI mode on this sytem(ga a75 ud4h)?  Windows media is the only media i can boot into EFI installer as intended allthough i did have to rebuild iso with winPE in order for an usable EFI image to be available.
Is it possible to rename directories on iso (rebuild iso) for Ubuntu?

The hardware being used failed the secure boot check when using the windows upgrade assistant but i am wondering if there is some kind of secure boot implementation as have seen "secure boot is not enabled" once or twice (unpredictable occurance).  But this could just be related to which flavour/distro is being booted to at install time.(shim) **EDIT: **This only happens when using an .iso with signed.efi image

---

### Post by oldfred on 2013-08-09
Boot-Repair does not add or delete partitions. It may tell you that it is needed, if converting from UEFI to BIOS boot. Ubuntu now does create a bios_grub partition. I only have BIOS and started using gpt with 10.10 and the installer did not create a bios_grub. I had to manually add that myself or grub would not install correctly on a gpt partitioned drive.

You only need an efi partition with UEFI boot or a bios_grub partition with BIOS boot, but I often suggest both if a new hard drive. Then you can install and all the partitions are there, or later you can change. Also if you install in BIOS mode and do not have an efi partition near beginning of drive it is difficult later to try to insert one when drive is full of data. Both are small compared to most new drives.

There just seem to be some systems that only boot the Windows efi file. That is a modification to the UEFI that is not UEFI standard. The only work around seems to be to install in BIOS mode and use Boot-Repair to rename the Windows efi file to actually be grub2's shim file which has the Microsoft signing key and still works. Then from grub menu you can boot the renamed/backed up Windows efi file.

       Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

    
Many vendors are fixing UEFI also, so updates to UEFI/BIOS may help resolve issues also.

---

### Post by Geezanansa on 2013-08-10
The hardware i have been using has been same from starting this little idea which is now a project of installing using EFI.  Mobo manufacturer no where in their documentation confirm which version of EFI is being used but it is EFI and not UEFI.

> Boot-Repair does not add or delete partitions. It may tell you that it is needed, if converting from UEFI to BIOS boot.

Using a 13.04 iso to install ubuntu would not start in efi mode at all for me i.e. **never** got black background grub list; **ever**.  I had to let the bios installer run and then used boot-repair to get Ubuntu booting using grub-efi and all this was without switching EFI off!

 <strike>_Boot-repair prompted me with commands to enter from terminal which included chrooting and am fairly sure a grub_bios partition was created on this fix.  i.e why was Ubuntu not booting if grub_bios was in existence.  So Ubuntu failed to start EFI and possibly did not create grub_bios partition.   boot-repair either fixed an unusable existing grub_bios or created it.  Have terminal log saved as text file if you would like to see it as well as evidence_</strike>  (**Edit: 12 August 2013** **re-reading this thread from begining prompted memory that it was 13.04 installer that requested the making of grub_bios partition and has nothing to do with boot-repair**)

 Boot-repair renamed the ubuntu EFI boot files to windows EFI boot files after backing up the original windows ones.
Using a 12.04 or 12.10 iso does start EFI mode but throws the can not read file and kernel needs to be loaded first errors so have be installed legacy mode and then install grub-efi to convert to using EFI.
Earlier flavours 11.04 11.10 apparently create a 16bit EFI partition. Which has to be recreated to 32bit before attempting to use it as 16bit is not EFI compliable i.e not part of EFI specification.  I have not had 11.04 or 11.10 running EFI mode on this hardware.

> There just seem to be some systems that only boot the Windows efi file.  That is a modification to the UEFI that is not UEFI standard.

It would appear i have hardware of the like as in having a very poor EFI implementation.
EFI specification is different from UEFI but EFI is essentialy UEFI. I prefer to use the EFI tag as that is what my machine describes it as.  EFI has not been collaboratly designed as it is purely Intels work with not much input from manufacturers.  Manufacturers are free to implement EFI on their hardware as they see fit or that is what my opinion is after doing some research.  My motherboard was manufactured in 2011.

Have had both Ubuntu installer and rEFInd mentioning files related to secure boot.  i.e.shim, amok, keys, signed image.  This is what implies some kind of secure boot implementation on the hardware being used.

> Many vendors are fixing UEFI also, so updates to UEFI/BIOS may help resolve issues also  AMD have ended the FM1 socket development. Motherboard manufacturer describes this model as entry level and have confirmed no development can be expected.  The firmware being used is a firmware version that is not available at their website and was obtained through their technical services department.

All this knowledge still has not enabled me to boot Ubuntu installer in EFI mode; ever.  That is not yet.:P

Am aware of firmware possibly looking for redhat and am working on a redhat install as part of the process of elemination..

---

### Post by Geezanansa on 2013-08-10
In engineering terms an unknown screw thread pitch is described as a bastard thread. It would appear i have a bastard EFI:eek:

---

### Post by oldfred on 2013-08-10
Just part of the issue of new technology and how well it is implemented. I was going to build a new system last summer, but I think with so many having issues is part of why I have not done it yet. Plus my 6 year old system still works for just about everything I do. 
Early UEFI versions of the Ubuntu installer & grub2 had all sorts of issues with partitions, configuration and just working. A few did get it to work, but the newer software works better and includes some work arounds for issues UEFI vendors had not fixed.

---

### Post by Geezanansa on 2013-08-11
This is my first motherboard that has EFI capabilities which is described as being entry level by manufacturers, whom are renowned for being one of the last of all the longer established manufacturers to provide this feature on their hardware.  Perhaps now that UEFI is a requisite for OEM installs of (a) newer and future operating systems this may actually be the turning point for UEFI going mainstream.  I find it remarkable this technology has been around for fifteen years plus and many machines have used it and are using it.   One point of interest (of the many fascinating stories of the history of EFI) i found was apparently it has been possible to boot a linux kernel since 2000 using EFI.  

Perhaps there may very well be another technology that comes along which proves so beneficial that everybody will actually want to use it due to undeniable advantages that it brings over previous technologies that are used to control the start up and management of our machines.

It is amazing how fast technologies do change and evolve.  For example how many people would have owned a wifi capable device ten years ago?  Not many more would have even been aware of the technology existed whereas now today the majority of the world population will be aware of it; with many actually being very dependent on wifi technology in order to live their daily lives and enjoy the advantages it brings.

Anyways my Ubuntu is not booting (can not mount filesystem errors) so have to go recreate a bios_grub partition.  heh heh

13.04 purrs like a kitten on this hardware.(as long as i dont muck about with bios_grub partitions)

Your tips thread oldfred (in your sig) is a great resource and brings to attention many things i have been overlooking especially regarding management of flash drives etc...

I find it fascinating you have not been converted to UEFI yet but do acknowledge a man of your experience and wisdom may well have own reasons not to whereas i am only taking the opportunity to learn and am trying to apply some of what i have been reading.

You have helped me along the way.  Thanks to you Ubuntu and Ubuntu Forums.

---

### Post by oldfred on 2013-08-11
I actually learned about UEFI before I built my system in 2006. But the only motherboards with UEFI back then were server systems that cost over $3000 or a lot more than I was spending on an entire system. So I have followed UEFI for quite a while and since thinking about new system last year started to follow all the issues so I would know how to install in my system. Still thinking about new system, but hopefully soon. :)

Just found this link. two previous videos in the series also are interesting but first is technical on boot keys and second it installing Windows 8 from scratch into a secure boot system.
       Intel - Install Ubuntu 12.10 part 3 of series for new system  w/secure boot, part one install keys, part 2 install Windows 8
[https://www.youtube.com/watch?v=_cEwj8bBBC4](https://www.youtube.com/watch?v=_cEwj8bBBC4)

---

### Post by Geezanansa on 2013-08-11
I wonder what $3000 could buy nowadays.  I was looking at MacPro towers just last night and nearly creamed my pants looking at the specs. Did not look at the prices though.

Have had a very interesting last few hours and have some questions and observations that i will try to convey regarding EFI booting on this machine.

OKay here we go.


[LIST]
[*]ref: bios_grub partition - Is this necessary purely for the purpose of booting Ubuntu when installed legacy mode next to an existing EFI install? 
[/LIST]

**Points of interest **-  After deleting bios_grub this machine was still booting both OS's.  However since doing this the Ubuntu filesytem has become corrupted and after fsck'ing still can not boot due to problems mounting filesystems.   Did try running boot-repair recommended fix first.  I did not have to change EFI off in BIOS for Boot-Repair to load and am pretty convinced it booted using EFI mode (which is a first) as i have never seen the wallpapers or desktop layout before that i was presented with.  When desktop loaded boot-repair confirmed detecting an EFI system and check settings.  After checking advanced options and starting boot-repair was warned legacy mode is selected and should check BIOS settings before rebooting to hard drive.  Which i did just to make sure my firmware had not reset or anything like that but EFI setting was confirmed. 
Recommended fix was applied from boot-repair - [http://paste.ubuntu.com/5975219](http://paste.ubuntu.com/5975219) After this and when rebooting grub menu appeared (whereas previously rEFInd was loading giving options of what can boot to).  Selecting Ubuntu from the new grub list gave```
 General error mounting filesystems. A maintenance shell will now be started.
```  If Ubuntu recovery was selected from grub list it gave ```
mountall:/lib/init/fstab: No such file or directory
```  To get to rEFInd the "Windows Boot UEFI Loader" was selected from grub list but Ubuntu options gave same results and Windows could not boot.
Seeing this as a grub problem i booted Super Grub2 Disc 2.00sl-beta5 which did find grub.cfg in sda4 as expected the kernel options look like ```
set params "(hd0,gpt4)/boot/grub/grub.cfg" "hd0,gpt4" "(hd0,gpt4)/boot/grub/grub.cfg" cfg_device="$2" cfg="$3" root="$cfg_device" "configfile"$cfg"
```

Still do not have working knowledge to confirm if this is obviously way out or not so admitted defeat and tried rebooting again just to see if icould find anything that i did understand!
After getting the same errors as mentioned here i dropped to command prompt and used ```
lsefisystab
``` to confirm grub/system could see/use efivars. This confirms my EFI as```
 revision 0002000a Vebndor TianoCore.org Version 10000001
```  rEFInd sees UEFI 2.1.

During doing all this also tried restoring Windows boot files using  windows installation media but only got to grub list with no bootable  options either directly from there or from rEFInd options when those  were selected from grub list.

So after this i thought i would try boot-repair again just to try something (running out of options) out of frustration.  Went through advanced settings (after booting EFI mode again!) and ran repair with some extra options including "fix filesystem".  here is BIS url [http://paste.ubuntu.com/5975450](http://paste.ubuntu.com/5975450) but now only ever get grub prompt when rebooting.

 

[LIST]
[*]Would the iso9660.x64.efi drivers that rEFInd installs allowed the EFI boot of boot-repair? 
[/LIST]
and if so ...
[LIST]
[*]Why don't these drivers boot Ubuntu media? 
[/LIST]


That was not as long winded as i thought it was going to be as i have four pages of notes here.  Hope have conveyed the gist!

---

### Post by oldfred on 2013-08-11
Is Windows hibernated? That is most often the issue with Windows 8 but  can be with Windows 7. Windows 8 is always hibernated as it has full hibernation and partial hibernation as the default shutdown or fastboot. 

You only need bios_grub for BIOS booting as that is where grub2 stores the core.img with gpt partitioning. With MBR it puts core.img in the sectors after the MBR but before first partition. But gpt does not have that space, so it just needs some unformatted space. Windows also requires its system reserved partition with gpt for the same reason as Windows would hide serial numbers, DRM info and some other info in the same sectors after MBR. And sometimes grub & Windows would fight for the same sector creating all sorts of boot issues.

I do not know about rEFInd. The creator posts in ask ubuntu forum.

If you have secure boot on system will only show systems that boot with secure boot or with signed kernels. With secure boot off, some have UEFI or CSM settings, so you know how you boot. But some will present either automatically or try UEFI and if that does not work then try BIOS mode and then if that does not work, give an error message.

---

### Post by Geezanansa on 2013-08-12
> Is Windows hibernated?  BIS from my last post says so but as previously posted (haven't changed a thing) have made sure all hiberbation and or fast boot settings in Windows are off.  What i am doing wrong is restarting and not powering off before booting anything else. (i think).

I have no way to confirm if there any secure boot specification implemented on this hardware due to no information regarding this from vendor as well as no media will boot using EFI mode or that is now with the exception of boot-repair and of course Windows media)  I just watched boot-repair trying to install and then uninstall grub-efi shim and the like but could not work out how to copy n paste from terminal to share that as well as BIS.  Did work it out after the needed info was not available.  kick.

I really do think this a grub problem.  Has been and still is. I used rEFInd as it is capable of doing more than what grub can as boot manager. Really do not mean to take away from from the vast undertaking of what grub has to do but there are definite design flaws.  And that is on top of the hardware being used which is probably very low on the grub devs hit list due to the very few people that are trying to use the EFI feature on this hardware. Which all adds to this accumulative error and not forgetting the bad user input as well!

Another contributing factor maybe that this hardware is a bios sytem with an emulated EFI = Hybrid EFI.  Most modern systems use a full UEFI with a legacy bios=CSM which is an emulated BIOS.  I think.   My hardware still describes booting without EFI mode with SATA set as AHCI as legacy.  Very confusing!  I am trying to explain what i think and not being deliberlately pedantic.  I really do think this a contributing factor as to why grub loader can not boot at boot time.  Which is the title of the thread.

BIS also says grub is in MBR!

I have no bootable OS (EFI or Legacy) as all that happens when booting is grub prompt.  That is booting to hard drive and optical drive! I simply disconnected the hard drive in order to enable booting a live session and posted here to try and update and ask for advice.  This is after running boot-repair twice with what i thought was EFI mode but terminal threw lots of errors when i followed the instruction so the fixes have never been applied. This will be i assume due to mount problems.  My tinkering about has led to current situation of only getting grub prompt.  I am posting this (and last post) from a live DVD "try Ubuntu" session.

---

### Post by Geezanansa on 2013-08-12
The answer to this question over at Ask Ubuntu may help get me back on track [http://askubuntu.com/a/331157/102029](http://askubuntu.com/a/331157/102029)  :D

---

### Post by oldfred on 2013-08-12
As I understand it rEFInd is a boot manager, it does not boot anything and still uses grub, Windows, or Mac to boot those systems.

Once you have installed grub in BIOS mode, Boot repair will always show the grub in the MBR. It never gets erased as if you ever want to fix it you just install a new copy. You then may not know if booting with UEFI or MBR, but if you have deleted bios_grub partition the grub in the MBR will not work. 
You can force erase of the MBR with dd and writing zeros but I would never recommend that as any typo can cause problems and having grub in MBR is not a problem.

---

### Post by Geezanansa on 2013-08-12
Using rEFInd as boot manager still uses grub boot loader to boot Ubuntu directly also with the option to load grub the boot manager at boot time.(grub option list without holding shift)  Going by your last post  looks to me it is grub deficcencies that are preventing the use of EFI to boot Ubuntu.  As you are saying if Ubuntu is installed using legacy will always use MBR even after grub-efi is installed.  ???

 I will look in earlier BIS that have linked to in this thread but am sure there is something more than not quite right going on here.  Also i can not boot any OS so again points to the MBR thing you reckon is not quite right.   How can a sytem use MBR when EFI is ON?   Am posting from a live session "try ubuntu" in order to get online.
Ref: "It never gets erased as if you ever want to fix it you just install a new copy." The EFI installer will not run as described  in first post. Therfore are you saying; "It is impossible to install using EFI on this machine. ?

I am trying to install Ubuntu using EFI and using boot-repair when system booted with EFI on is confirmed by boot-repair as a window with "EFI is detected check your settings" confirms The recommended repair then confirms the installation of grub-efi but then says "legacy mode detected be sure to boot to /boot/EFI....  "

Yuck. Is this a grub bug?  I am only using boot-repair because of installers inability to run in EFI mode.  The boot-repair thing of installing grub-efi is a work around.


Will email yannubuntu links of BIS in order to try and get their input as well and contact the author of rEFInd directly to see if this matter can be explained if not fixed!

---

### Post by Geezanansa on 2013-08-12
Another useful resource created by rEFInd's author is a  set of tools that come with gdisk which includes fixparts.  Had been running  these in order to try and learn how to use them.  I wonder if i have inadvertently caused this situation..  Another reason to contact author...

---

### Post by Geezanansa on 2013-08-12
After switching off EFI and booting Parted Magic parted sees my now reconnected drive as
```
Type device filename, or press <Enter> to exit: 
root@partedmagic:~# sudo parted -l
Model: ATA WDC WD1001FALS-4 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system     Name                                 Flags
 1      1049kB  233MB  232MB   fat32           EFI system partition                 boot
 2      233MB   366MB  133MB                   Microsoft reserved partition         msftres
 3      368MB   269GB  268GB   ntfs
 4      269GB   371GB  102GB   ext4
 6      371GB   379GB  8193MB  linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Invalid partition table - recursive partition on /dev/sr0.

```

Looks like whatever recursive partition means is triggering the partition outside disk in BIS.

Looking at rodsbooks page on fixparts confirms this is a MBR disk tool.  So am now working with gdisk to hopefuly get booting from hard drive again...

parted has just slapped me with more relevant info in getting a solution to "How to get  installation media to boot  in EFI mode?".

```
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Invalid partition table - recursive partition on /dev/sr0.
Ignore/Cancel? i                                                          
Model: TSSTcorp CDDVDW SH-S223C (scsi)
Disk /dev/sr0: 330MB
Sector size (logical/physical): 2048B/2048B
Partition Table: msdos
Disk Flags: 

Number  Start  End  Size  Type  File system  Flags

```

msdos partition is never going to boot using EFI ... or is it msdos because EFI was switched off?

---

### Post by Geezanansa on 2013-08-12
What i have done to get Windows booting;


[LIST]
[*]Booted Parted Magic cd (with EFI off due to "you need to load kernel first" error(s)) 
[/LIST]
 
[LIST]
[*]Used gdisk to verify EFI partition and wrote to disk 
[/LIST]
 which gave grub prompt only after rebooting 

[LIST]
[*]rebooted using rEFInd cd 
[/LIST]
 
[LIST]
[*]Selected Windows option 
[/LIST]
 BOOM 3 secs later logged in to windows

Is grub the problem as boot manager?  I am  more than convinced it is.  rEFInd saved the day (and gdisk) 

How much i would like to stomp grub the boot manager to death  and then burn the remains i can not start to convey...

Now i need to start working on how to fix my bootloaders so that rEFInd has full control as boot manager again.  It would appear grub has been and is a hugely incompetent mess...
Why most distributions use i do not know.

Looks like i have found a superior option.  Thank you for rEFInd.

---

### Post by oldfred on 2013-08-12
Issues with sr0 are the CD or DVD.

---

### Post by Geezanansa on 2013-08-15
Would like to clear up my refernces to bios_grub partition regarding boot troubles with Ubuntu when EFI is being used after grub-efi is installed.  Even rereading my post [http://ubuntuforums.org/showthread.php?t=2149013&p=12751959#post12751959](http://ubuntuforums.org/showthread.php?t=2149013&p=12751959#post12751959) of this thread indicates i keep on changing attitude.(desperation to come to some kind of understanding of what is going on here with regard to as why Ubuntu installtion media will not or can not boot using EFI mode ).

Running boot-repair recommended fixes (to fix Ubuntu boot) have become impossible due to the errors listed in [http://ubuntuforums.org/showthread.php?t=2149013&p=12753718#post12753718](http://ubuntuforums.org/showthread.php?t=2149013&p=12753718#post12753718)

rEFInd was working for me again without cd but the only boot option that loaded anything was Windows- "Boot Microsoft EFI boot from SYSTEM"

In an attempt to get Ubuntu added to windows boot manager for the option to try and boot Ubuntu at boot time when selecting Windows from rEFInd options.-  Did this using something like ```
bcdboot {bootmgr} \grub\grubx64.efi
```  again another act of desperation ie why did i expect Ubuntu to boot through windows if it was not through rEFInd???? i do not know .  The result of which is Windows boot loader has been raped once again...

Additionally tried installing latest release of Fedora (as it is associated with redhat to try and see if installer runs in EFI mode on this hardware with EFI ON- which in fact it did....)


So what have i got now? ....

Well in a nutshell [http://paste.ubuntu.com/5990061](http://paste.ubuntu.com/5990061)   

When booting boot-repair-disk it does still boot  with EFI on but on loading desktop get "RAID is detected install mdad...."  and hangs ...  eventually giving the "EFI is detected" window  and am sure if repair is ran it would tell me "legacy mode is detected please check your settings and make sure..."  Have paraphrased from memory here but have mentioned the "EFI  detected" and then getting the "legacy detected" when recommended fix runs in an earlier post [http://ubuntuforums.org/showthread.php?t=2149013&p=12753718#post12753718](http://ubuntuforums.org/showthread.php?t=2149013&p=12753718#post12753718) in the paragraph marked as **Points of interest-**
Is this grub bug(s)?
Is this firmware bug(s)?
How can i constructively use some of the information being amassed here?
Is time to admit defeat trying to use linux with EFI on this machine?

---

### Post by oldfred on 2013-08-15
Fedora uses LVM as a default. If multiple booting and do not have entire drive as LVM, it offers little advantage. Many just install Fedora with standard partitions, but you have to change that as you install.

Ubuntu Desktop does not have LVM drivers installed by default. So from Ubuntu you may not see LVM partitions. Boot-Repair cannot easily tell LVM from RAID as both use /dev/mapper/..., Boot-Repair may have installed the lvm2 driver in the version you ran it from, but may not know if you also need RAID?
       sudo apt-get install lvm2

Are you Booting Boot-Repair in legacy mode or UEFI mode. Best to be in UEFI mode if you want UEFI. It  tells you this:

> The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.

---

### Post by Geezanansa on 2013-08-16
> Are you Booting Boot-Repair in legacy mode or UEFI mode.?   

Good question.  I have booted boot-repair-disc with EFI mode on.
 Due to mixture of messages boot-repair is giving me and the fact no other media boots (with the exception of Windows installation media) i am wondering if boot-repair has efi booter and bios booter images in order to work on both settings.  How could i concretely confirm which mode the boot-repair disc is actually using?

What i have seen and what i have done is after making sure EFI is on and  booting boot-repair is  boot-repair gave me the "RAID is detected install mdad...."  and hangs ...  eventually giving  the "EFI is detected" window  and then "legacy mode is detected please check your settings and make  sure..."   I double checked firmware settings after getting url for boot info script.  There was no RAID settings set. EFI is on. SATA is set as AHCI.  Which i tried to describe in my last post.

Ubuntu installer is a mess but Fedora has absolutely wiped EFI directory and created some wierd and wonderful parttion table.  

Think i have found something that goes to some way explaining ubuntu installer problem on this hardware.
Since 12.10 using shiim which was backported to 12.04.2 the first stage installer is looking for signed.efi image or shim is assigned to do this if secure boot is enabled the second stage installer then is used.  I have not made this up either.  see here [http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)
I am not sure of the intended meaning of first stage and second stage installers that are mentioned there.
Looks to me as rEFInd sees installation media BIIOS installer as Fallback loader so the conclusion is "you need to load kernel first " is given because EFI is on and installer is looking to use signed.efi image and can not because Secure Boot is not enabled which then triggers fall back to BIOS installer.  but would prefer if it if somebody can say what is happening or what is needed in order to rather than me trying to explain what i think is happening.  

I partitioned drive with intention of using 100GB for Fedora but once installed updates would not install and when i tried to reboot it dropped to maintenace shell with very similar symptons/errors as Ubuntu so tried using Fedora installer to delete the bad install and tried again which gave the very unusual partitioning layout leaving 57GB / from initial attempt.  It also made small bios parttion which indicates what i thought was EFI installer running is not as EFI was again definitely on.


I can not install any packages to ubuntu due to mountall error listed in the post i linked to in my last post. Boot-repair asked me to install mdadmn or something but can not because of corrupted drive fsck can not run no recovery just grub prompt or maintenance shell this is with 13.04 install. How can i go about fixing the mountall errors i have asked about in order to get grub reinstalled to the correct place?  That was before trying to install Fedora.  Nothing is bootable Fedoras boot manager has taken over. No refind no windows no ubuntu no fedora will boot. Nothing. 

Posting this from bios live sess. 13.04

The way parted sees my drive is 
```
Model: ATA WDC WD1001FALS-4 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name                                 Flags
 1      1049kB  233MB  232MB   fat32           EFI system partition                 boot
 2      233MB   366MB  133MB                   Microsoft reserved partition         msftres
 6      366MB   367MB  1049kB                                                       bios_grub
 3      368MB   269GB  268GB   ntfs
 4      269GB   371GB  102GB   ext4
 5      371GB   379GB  8193MB  linux-swap(v1)
 7      379GB   380GB  524MB   ext4
 8      380GB   581GB  201GB                                                        lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora_ubuntuuser--ga--a75--ud4h-root: 53.7GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  53.7GB  53.7GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora_ubuntuuser--ga--a75--ud4h-swap: 7936MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  7936MB  7936MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/fedora_ubuntuuser--ga--a75--ud4h-home: 139GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  139GB  139GB  ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!     
```

---

### Post by oldfred on 2013-08-16
When you boot Boot-Repair in BIOS mode you should get the accessibility icons (little keyboard & person icons which mean to press a key if you need help). 
If booting in UEFI mode all you get is grub menu.

---

### Post by Geezanansa on 2013-08-16
After selecting DVD from one time boot options i get a black screen then a nice blue screen with boot-repair-disk written in middle of screen with a loading progress bar very similar to plymouth (bootsplash i think)O:)that is with EFI on.  I downloaded .iso from [http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/) and find it boots slightly quicker than Ubuntu and saves having to install boot- repair after booting live session.;)
Have just filed my first "bug" [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1213119](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1213119) should have had it under linux instead of grub2 i thinks especially considering mountall errors which i do think is associated with workaround to get Ubuntu booting using EFI .

---

### Post by Geezanansa on 2013-08-16
:redface:
>                               [INDENT]                     When you boot Boot-Repair in BIOS mode you should get the  accessibility icons (little keyboard & person icons which mean to  press a key if you need help). 
If booting in UEFI mode all you get is grub menu.        
[/INDENT]
            
                         
                                                                          i am not sure what you are describing here do you mean when booting Ubuntu liveDVD?

What i have already described when trying to explain what i have done when booting a boot-repair-disc and other observations:

>                               Are you Booting Boot-Repair in legacy mode or UEFI mode.?                            Good question.  I have booted boot-repair-disc with EFI mode on.
 Due to mixture of messages boot-repair is giving me and the fact no  other media boots (with the exception of Windows installation media) i  am wondering if boot-repair has efi booter and bios booter images in  order to work on both settings.  How could i concretely confirm which  mode the boot-repair disc is actually using?

What i have seen and what i have done is after making sure EFI is on and   booting boot-repair is  boot-repair gave me the "RAID is detected  install mdad...."  and hangs ...  eventually giving  the "EFI is  detected" window  and then "legacy mode is detected please check your  settings and make  sure..."   I double checked firmware settings after  getting url for boot info script.  There was no RAID settings set. EFI  is on. SATA is set as AHCI.  Which i tried to describe in my last post.

Ubuntu installer is a mess but Fedora has absolutely wiped EFI directory and created some wierd and wonderful parttion table.  

Think i have found something that goes to some way explaining ubuntu installer problem on this hardware.
Since 12.10 using shiim which was backported to 12.04.2 the first stage  installer is looking for signed.efi image or shim is assigned to do this  if secure boot is enabled the second stage installer then is used.  I  have not made this up either.  see here [http://web.dodds.net/~vorlon/wiki/bl..._Ubuntu_12.10/]("http://web.dodds.net/%7Evorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")
I am not sure of the intended meaning of first stage and second stage installers that are mentioned there.
Looks to me as rEFInd sees installation media BIIOS installer as  Fallback loader so the conclusion is "you need to load kernel first " is  given because EFI is on and installer is looking to use signed.efi  image and can not because Secure Boot is not enabled which then triggers  fall back to BIOS installer.  but would prefer if it if somebody can  say what is happening or what is needed in order to rather than me  trying to explain what i think is happening.  

---

### Post by Geezanansa on 2013-08-16
Can only boot Ubuntu 13.04 after switching EFI off by selecting NON EFI.  I decided to try booting boot-repair disk with these settings to see what the result would be.  What happened was after selecting language then UK key map got the blue boot splash screen until desktop loaded.  Was greeted with the RAID detected window which i okayed and os prober took a while until another box saying EFI detected ...." so after reviewing advanced options and making sure Ubuntu (sda4)set as default OS and boot/EFI(sda1) as grub location were selected Applying these gave window stating "legacy detected make sure to check settings you may want to retry after doing this do you want to continue?" I selected no and rebooted to bios settings reselecting EFI.  
After rebooting and repeating the process. 
Lubuntu desktop loaded and was greeted with the RAID detected window which was okayed.  OSprober took a while before EFI detected window appeared. After reviewing advanced options again selecting sda4 Ubuntu as default OS and boot/EFI sda1 as grub location. When applying these settings was requested to enter a series of commands. I managed to save a copy of these and it went like so:
```
lubuntu@lubuntu:~$ sudo chroot "/mnt/boot-sav/sda4" dpkg --configure -a
dpkg: dependency problems prevent configuration of grub-efi-amd64-bin:
 grub-efi-amd64-bin depends on grub-common (= 2.00-13ubuntu3); however:
  Package grub-common is not configured yet.

dpkg: error processing grub-efi-amd64-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.00-13ubuntu3); however:
  Package grub-common is not configured yet.

dpkg: error processing grub2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi:
 grub-efi depends on grub-common; however:
  Package grub-common is not configured yet.

dpkg: error processing grub-efi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi-amd64:
 grub-efi-amd64 depends on grub-common; however:
  Package grub-common is not configured yet.
 grub-efi-amd64 depends on grub2-common (= 2.00-13ubuntu3); however:
  Package grub2-common is not configured yet.
 grub-efi-amd64 depends on grub-efi-amd64-bin (= 2.00-13ubuntu3); however:
  Package grub-efi-amd64-bin is not configured yet.

dpkg: error processing grub-efi-amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub-efi-amd64-bin
 grub2-common
 grub-efi
 grub-efi-amd64
lubuntu@lubuntu:~$ sudo chroot "/mnt/boot-sav/sda4" apt-get install -fy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libavahi-client3:i386 libavahi-common-data:i386
  libavahi-common3:i386 libcapi20-3:i386 libcups2:i386 libexif12:i386
  libflac8:i386 libfontconfig1:i386 libfreetype6:i386 libgcrypt11:i386
  libgd2-xpm:i386 libgif4:i386 libglu1-mesa:i386 libgnutls26:i386
  libgpg-error0:i386 libgphoto2-2:i386 libgphoto2-port0:i386
  libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhx509-5-heimdal:i386 libice6:i386 libieee1284-3:i386
  libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms1:i386 libldap-2.4-2:i386 libltdl7:i386
  libmpg123-0:i386 libogg0:i386 libopenal1:i386 liborc-0.4-0:i386
  libp11-kit-gnome-keyring:i386 libp11-kit0:i386 libpulse0:i386
  libroken18-heimdal:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsm6:i386 libsndfile1:i386 libspeexdsp1:i386
  libsqlite3-0:i386 libssl1.0.0:i386 libtasn1-3:i386 libtiff5:i386
  libusb-0.1-4:i386 libusb-1.0-0:i386 libv4l-0:i386 libv4lconvert0:i386
  libvorbis0a:i386 libvorbisenc2:i386 libwind0-heimdal:i386 libwrap0:i386
  libxcomposite1:i386 libxcursor1:i386 libxi6:i386 libxinerama1:i386
  libxml2:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxslt1.1:i386
  libxt6:i386 wine-gecko1.4:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-common (2.00-13ubuntu3) ...
/etc/init.d/grub-common: 17: .: Can't open /lib/init/vars.sh
invoke-rc.d: initscript grub-common, action "start" failed.
dpkg: error processing grub-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.00-13ubuntu3); however:
  Package grub-common is not configured yet.

dpkg: error processing grub2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi-amd64-bin:
 grub-efi-amd64-bin depends on grub-common (= 2.00-13ubuntu3); however:
  Package grub-common is not configured yet.

dpkg: error processing grub-efi-amd64-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi-amd64:
 grub-efi-amd64 depends on grub-common; however:
  Package grub-common is not configured yet.
 grub-efi-amd64 depends on grub2-common (= 2.00-13ubuntu3); however:
  Package grub2-common is not configured yet.
 grub-efi-amd64 depends on grub-efi-amd64-bin (= 2.00-13ubuntu3); however:
  Package grub-efi-amd64-bin is not configured yet.

dpkg: error processing grub-efi-amd64 No apport report written because the error message indicates its a followup error from a previous failure.
                                                                No apport report written because the error message indicates its a followup error from a previous failure.
          No apport report written because MaxReports is reached already
                                                                        No apport report written because MaxReports is reached already
                                                      (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi:
 grub-efi depends on grub-common; however:
  Package grub-common is not configured yet.
 grub-efi depends on grub-efi-amd64 (= 2.00-13ubuntu3); however:
  Package grub-efi-amd64 is not configured yet.

dpkg: error processing grub-efi (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub-common
 grub2-common
 grub-efi-amd64-bin
 grub-efi-amd64
 grub-efi
E: Sub-process /usr/bin/dpkg returned an error code (1)
lubuntu@lubuntu:~$ sudo chroot "/mnt/boot-sav/sda4" apt-get install -y --force-yes dmraid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libavahi-client3:i386 libavahi-common-data:i386
  libavahi-common3:i386 libcapi20-3:i386 libcups2:i386 libexif12:i386
  libflac8:i386 libfontconfig1:i386 libfreetype6:i386 libgcrypt11:i386
  libgd2-xpm:i386 libgif4:i386 libglu1-mesa:i386 libgnutls26:i386
  libgpg-error0:i386 libgphoto2-2:i386 libgphoto2-port0:i386
  libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhx509-5-heimdal:i386 libice6:i386 libieee1284-3:i386
  libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms1:i386 libldap-2.4-2:i386 libltdl7:i386
  libmpg123-0:i386 libogg0:i386 libopenal1:i386 liborc-0.4-0:i386
  libp11-kit-gnome-keyring:i386 libp11-kit0:i386 libpulse0:i386
  libroken18-heimdal:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsm6:i386 libsndfile1:i386 libspeexdsp1:i386
  libsqlite3-0:i386 libssl1.0.0:i386 libtasn1-3:i386 libtiff5:i386
  libusb-0.1-4:i386 libusb-1.0-0:i386 libv4l-0:i386 libv4lconvert0:i386
  libvorbis0a:i386 libvorbisenc2:i386 libwind0-heimdal:i386 libwrap0:i386
  libxcomposite1:i386 libxcursor1:i386 libxi6:i386 libxinerama1:i386
  libxml2:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxslt1.1:i386
  libxt6:i386 wine-gecko1.4:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  watershed
The following NEW packages will be installed:
  lvm2 watershed
0 upgraded, 2 newly installed, 0 to remove and 11 not upgraded.
5 not fully installed or removed.
Need to get 538 kB of archives.
After this operation, 1,293 kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu/ raring/main watershed amd64 7 [11.4 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ raring/main lvm2 amd64 2.02.95-6ubuntu4 [527 kB]
Fetched 538 kB in 0s (877 kB/s)
Selecting previously unselected package watershed.
(Reading database ... 164928 files and directories currently installed.)
Unpacking watershed (from .../archives/watershed_7_amd64.deb) ...
Selecting previously unselected package lvm2.
Unpacking lvm2 (from .../lvm2_2.02.95-6ubuntu4_amd64.deb) ...
Processing triggers for man-db ...
Setting up grub-common (2.00-13ubuntu3) ...
/etc/init.d/grub-common: 17: .: Can't open /lib/init/vars.sh
invoke-rc.d: initscript grub-common, action "start" failed.
dpkg: error processing grub-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.00-13ubuntu3); however:
  Package grub-common is not configured yet.

dpkg: error processing grub2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi-amd64-bin:
 grub-efi-amd64-bin depends on grub-common (= 2.00-13ubuntu3); however:
  Package grub-common is not configured yet.

dpkg: error processing grub-efi-amd64-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi-amd64:
 grub-efi-amd64 depends on grub-common; however:
  Package grub-common is not configured yet.
 grub-efi-amd64 depends on grub2-common (= 2.00-13ubuntu3); however:
  Package grub2-common is not configured yet.
 grub-efi-amd64 depends on grub-efi-amd64-bin (= 2.00-13ubuntu3); however:
  Package grub-efi-amd64-bin is not configured yet.

dpkg: error processing grub-efi-amd64 No apport report written because the error message indicates its a followup error from a previous failure.
                                                                No apport report written because the error message indicates its a followup error from a previous failure.
          No apport report written because MaxReports is reached already
                                                                        No apport report written because MaxReports is reached already
                                                      (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-efi:
 grub-efi depends on grub-common; however:
  Package grub-common is not configured yet.
 grub-efi depends on grub-efi-amd64 (= 2.00-13ubuntu3); however:
  Package grub-efi-amd64 is not configured yet.

dpkg: error processing grub-efi (--configure):
 dependency problems - leaving unconfigured
Setting up watershed (7) ...
update-initramfs: deferring update (trigger activated)
Setting up lvm2 (2.02.95-6ubuntu4) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-28-generic
Errors were encountered while processing:
 grub-common
 grub2-common
 grub-efi-amd64-bin
 grub-efi-amd64
 grub-efi
E: Sub-process /usr/bin/dpkg returned an error code (1)
lubuntu@lubuntu:~$ sudo chroot "/mnt/boot-sav/sda4" apt-get purge -y --force-yes grub*-common shim-signed linux-signed*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'grub-common' for regex 'grub*-common'
Note, selecting 'linux-signed-image-3.8.0-20-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.8.0-23-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.8.0-26-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.8.0-29-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.8.0-21-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.8.0-24-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.8.0-19-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.8.0-27-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.8.0-22-generic' for regex 'linux-signed*'
Note, selecting 'efilinux-signed' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.8.0-25-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-3.8.0-28-generic' for regex 'linux-signed*'
Package 'shim-signed' is not installed, so not removed
Package 'efilinux-signed' is not installed, so not removed
Package 'linux-signed-image-3.8.0-19-generic' is not installed, so not removed
Package 'linux-signed-image-3.8.0-21-generic' is not installed, so not removed
Package 'linux-signed-image-3.8.0-22-generic' is not installed, so not removed
Package 'linux-signed-image-3.8.0-23-generic' is not installed, so not removed
Package 'linux-signed-image-3.8.0-25-generic' is not installed, so not removed
Package 'linux-signed-image-3.8.0-26-generic' is not installed, so not removed
Package 'linux-signed-image-3.8.0-27-generic' is not installed, so not removed
Package 'linux-signed-generic' is not installed, so not removed
Package 'linux-signed-image-3.8.0-20-generic' is not installed, so not removed
Package 'linux-signed-image-3.8.0-24-generic' is not installed, so not removed
Package 'linux-signed-image-3.8.0-28-generic' is not installed, so not removed
Package 'linux-signed-image-3.8.0-29-generic' is not installed, so not removed
Package 'linux-signed-image-generic' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libavahi-client3:i386 libavahi-common-data:i386
  libavahi-common3:i386 libcapi20-3:i386 libcups2:i386 libexif12:i386
  libflac8:i386 libfontconfig1:i386 libfreetype6:i386 libgcrypt11:i386
  libgd2-xpm:i386 libgif4:i386 libglu1-mesa:i386 libgnutls26:i386
  libgpg-error0:i386 libgphoto2-2:i386 libgphoto2-port0:i386
  libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhx509-5-heimdal:i386 libice6:i386 libieee1284-3:i386
  libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms1:i386 libldap-2.4-2:i386 libltdl7:i386
  libmpg123-0:i386 libogg0:i386 libopenal1:i386 liborc-0.4-0:i386
  libp11-kit-gnome-keyring:i386 libp11-kit0:i386 libpulse0:i386
  libroken18-heimdal:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsm6:i386 libsndfile1:i386 libspeexdsp1:i386
  libsqlite3-0:i386 libssl1.0.0:i386 libtasn1-3:i386 libtiff5:i386
  libusb-0.1-4:i386 libusb-1.0-0:i386 libv4l-0:i386 libv4lconvert0:i386
  libvorbis0a:i386 libvorbisenc2:i386 libwind0-heimdal:i386 libwrap0:i386
  libxcomposite1:i386 libxcursor1:i386 libxi6:i386 libxinerama1:i386
  libxml2:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxslt1.1:i386
  libxt6:i386 wine-gecko1.4:i386
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub-common* grub-efi* grub-efi-amd64* grub-efi-amd64-bin* grub2-common*
0 upgraded, 0 newly installed, 5 to remove and 11 not upgraded.
5 not fully installed or removed.
After this operation, 8,234 kB disk space will be freed.
(Reading database ... 165045 files and directories currently installed.)
Removing grub-efi ...
Removing grub-efi-amd64 ...
Purging configuration files for grub-efi-amd64 ...
Removing grub2-common ...
Removing grub-efi-amd64-bin ...
Removing grub-common ...
/etc/init.d/grub-common: 17: .: Can't open /lib/init/vars.sh
invoke-rc.d: initscript grub-common, action "stop" failed.
dpkg: error processing grub-common (--purge):
 subprocess installed pre-removal script returned error exit status 2
/etc/init.d/grub-common: 17: .: Can't open /lib/init/vars.sh
invoke-rc.d: initscript grub-common, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Processing triggers for man-db ...
Processing triggers for install-info ...
Errors were encountered while processing:
 grub-common
E: Sub-process /usr/bin/dpkg returned an error code (1)




lubuntu@lubuntu:~$ sudo chroot "/mnt/boot-sav/sda4" apt-get install -y --force-yes grub-efi linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libasn1-8-heimdal:i386 libasound2:i386 libasound2-plugins:i386
  libasyncns0:i386 libavahi-client3:i386 libavahi-common-data:i386
  libavahi-common3:i386 libcapi20-3:i386 libcups2:i386 libexif12:i386
  libflac8:i386 libfontconfig1:i386 libfreetype6:i386 libgcrypt11:i386
  libgd2-xpm:i386 libgif4:i386 libglu1-mesa:i386 libgnutls26:i386
  libgpg-error0:i386 libgphoto2-2:i386 libgphoto2-port0:i386
  libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhx509-5-heimdal:i386 libice6:i386 libieee1284-3:i386
  libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms1:i386 libldap-2.4-2:i386 libltdl7:i386
  libmpg123-0:i386 libogg0:i386 libopenal1:i386 liborc-0.4-0:i386
  libp11-kit-gnome-keyring:i386 libp11-kit0:i386 libpulse0:i386
  libroken18-heimdal:i386 libsamplerate0:i386 libsane:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsm6:i386 libsndfile1:i386 libspeexdsp1:i386
  libsqlite3-0:i386 libssl1.0.0:i386 libtasn1-3:i386 libtiff5:i386
  libusb-0.1-4:i386 libusb-1.0-0:i386 libv4l-0:i386 libv4lconvert0:i386
  libvorbis0a:i386 libvorbisenc2:i386 libwind0-heimdal:i386 libwrap0:i386
  libxcomposite1:i386 libxcursor1:i386 libxi6:i386 libxinerama1:i386
  libxml2:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxslt1.1:i386
  libxt6:i386 wine-gecko1.4:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-efi-amd64 grub-efi-amd64-bin grub2-common
The following NEW packages will be installed:
  grub-efi grub-efi-amd64 grub-efi-amd64-bin grub2-common
The following packages will be upgraded:
  linux
1 upgraded, 4 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
Need to get 2,832 B/711 kB of archives.
After this operation, 2,614 kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu/ raring-proposed/main linux amd64 3.8.0.29.47 [1,690 B]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ raring/main grub-efi amd64 2.00-13ubuntu3 [1,142 B]
Fetched 2,832 B in 0s (24.5 kB/s)     
Preconfiguring packages ...
Selecting previously unselected package grub2-common.
(Reading database ... 164802 files and directories currently installed.)
Unpacking grub2-common (from .../grub2-common_2.00-13ubuntu3_amd64.deb) ...
Preparing to replace linux 3.8.0.28.46 (using .../linux_3.8.0.29.47_amd64.deb) ...
Unpacking replacement linux ...
Selecting previously unselected package grub-efi-amd64-bin.
Unpacking grub-efi-amd64-bin (from .../grub-efi-amd64-bin_2.00-13ubuntu3_amd64.deb) ...
Selecting previously unselected package grub-efi-amd64.
Unpacking grub-efi-amd64 (from .../grub-efi-amd64_2.00-13ubuntu3_amd64.deb) ...
Selecting previously unselected package grub-efi.
Unpacking grub-efi (from .../grub-efi_2.00-13ubuntu3_amd64.deb) ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Setting up grub-common (2.00-13ubuntu3) ...
/etc/init.d/grub-common: 17: .: Can't open /lib/init/vars.sh
invoke-rc.d: initscript grub-common, action "start" failed.
dpkg: error processing grub-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.00-13ubuntu3); however:
  Package grub-common is not configured yet.

dpkg: error processing grub2-common (--configure):
 dependency problems - leaving unconfigured
Setting up linux (3.8.0.29.47) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of grub-efi-amd64-bin:
 grub-efi-amd64-bin depends on grub-common (= 2.00-13ubuntu3); however:
  Package grub-common is not configured yet.

dpkg: error processing grub-efi-amd64-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of grub-efi-amd64:
 grub-efi-amd64 depends on grub-common; however:
  Package grub-common is not configured yet.
 grub-efi-amd64 depends on grub2-common (= 2.00-13ubuntu3); however:
  Package grub2-common is not configured yet.
 grub-efi-amd64 depends on grub-efi-amd64-bin (= 2.00-13ubuntu3); however:
  Package grub-efi-amd64-bin is not configured yet.

dpkg: error processing grub-efi-amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub-efi:
 grub-efi depends on grub-common; however:
  Package grub-common is not configured yet.
 grub-efi depends on grub-efi-amd64 (= 2.00-13ubuntu3); however:
  Package grub-efi-amd64 is not configured yet.

dpkg: error processing grub-efi (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 grub-common
 grub2-common
 grub-efi-amd64-bin
 grub-efi-amd64
 grub-efi
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The bootinfoscript url that was generated is [http://paste.ubuntu.com/5994783/](http://paste.ubuntu.com/5994783/)

Trying to identify which boot mode boot-repair disc is using i tried looking for efivars but could not find 
```
lubuntu@lubuntu:~$ lsmod
Module                  Size  Used by
btrfs                 785967  0 
zlib_deflate           26885  1 btrfs
ufs                    74597  0 
qnx4                   13317  0 
hfsplus                88539  0 
hfs                    54503  0 
minix                  36072  0 
ntfs                   96967  0 
msdos                  17332  0 
jfs                   185045  0 
xfs                   869118  0 
libcrc32c              12615  2 xfs,btrfs
reiserfs              241608  0 
ext2                   72837  0 
dm_crypt               22820  0 
snd_hda_codec_realtek    78399  1 
snd_hda_codec_hdmi     36913  1 
snd_hda_intel          39619  0 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
kvm                   443165  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
k10temp                13126  0 
snd_timer              29425  1 snd_pcm
snd                    68876  7 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_hda_codec,snd_hda_intel
soundcore              12680  1 snd
serio_raw              13215  0 
i2c_piix4              13266  0 
mac_hid                13205  0 
dm_multipath           22843  0 
microcode              22881  0 
scsi_dh                14843  1 dm_multipath
squashfs               36522  1 
overlayfs              28003  1 
nls_utf8               12557  1 
isofs                  39815  1 
nls_iso8859_1          12713  0 
dm_raid45              76725  0 
xor                    17116  1 dm_raid45
dm_mirror              21946  0 
dm_region_hash         20820  1 dm_mirror
dm_log                 18529  3 dm_region_hash,dm_mirror,dm_raid45
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
radeon                937749  2 
i2c_algo_bit           13413  1 radeon
ttm                    83187  1 radeon
r8169                  67446  0 
drm_kms_helper         49394  1 radeon
drm                   286313  4 ttm,drm_kms_helper,radeon
ahci                   25731  3 
libahci                31364  1 ahci



```

---

### Post by oldfred on 2013-08-16
Where did RAID come from? That often causes issues unless you really are running RAID and have installed the RAID drivers to install grub correctly.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

### Post by Geezanansa on 2013-08-16
The reason why boot-repair-disk is doing this is probably directly related to why i can not boot any Grub options when trying to install using EFI.

It would appear due to the fact there is no Windows boot loader or manager in /boot/EFI in order for boot-repair to rename is causing more than a problem for installing grub-efi and that is not considering the issue with mountall....

How do i get Ubuntu booting using EFI?  How do i get DVD media booting using EFI?

---

### Post by oldfred on 2013-08-17
It seems like your older Gigabyte board just is not fully UEFI compatible. That may be why rEFInd works or helps. I think he somewhere mentioned using UEFI with BIOS as a way to test UEFI on BIOS type systems.

 [https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

---

### Post by Geezanansa on 2013-08-17
> **oldfred said:**
> Fedora uses LVM as a default. If multiple booting and do not have entire drive as LVM, it offers little advantage. Many just install Fedora with standard partitions, but you have to change that as you install.

Ubuntu Desktop does not have LVM drivers installed by default. So from Ubuntu you may not see LVM partitions. Boot-Repair cannot easily tell LVM from RAID as both use /dev/mapper/..., Boot-Repair may have installed the lvm2 driver in the version you ran it from, but may not know if you also need RAID?
       sudo apt-get install lvm2

Are you Booting Boot-Repair in legacy mode or UEFI mode. Best to be in UEFI mode if you want UEFI. It  tells you this:
and then you ask
> **oldfred said:**
> Where did RAID come from? That often causes  issues unless you really are running RAID and have installed the RAID  drivers to install grub correctly.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

The mention of RAID i thought was due to Fedora using LVM as default when trying to install Fedora.  Fedora only rebooted once after installing and broke when trying to update.  Nothing is bootable.  Fedora, Ubuntu or Windows.

Nothing is installable to Ubuntu due to maintenance shell  being activated due to mountall problems.  Have posted terminal output to inducate the type of errors thrown when trying to install anything.  Have absolutely no working knowledge of Fedora so ideally would like to remove those partitions.

---

### Post by Geezanansa on 2013-08-17
rEFInd can not see any usable efi bootloaders.  This hardware is a full bios system with an emulated EFI layer.  Which means i do not have the necessary CSM to let rEFInd see msdos bootloaders as this is not an UEFI system..

How do i get the efi bootloaders back to where they should be? ref last BIS [http://paste.ubuntu.com/5994783/](http://paste.ubuntu.com/5994783/)

---

### Post by Geezanansa on 2013-08-17
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)  very interesting

---

### Post by oldfred on 2013-08-17
I do not really know LVM, but know gparted does not work with it. Although I thought I saw something where the very newest gparted may, but that is not in Ubuntu.
       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

You normally use lvm tools for LVM.
      
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay

You have an efi partition, and grub still in protective MBR.

---

### Post by Geezanansa on 2013-08-17
Here is a small quote from the link
[QUOTE][**3.2 Ubuntu x86_64 ISO**

  **3.2.1** Extract the Ubuntu x86_64 iso into [MOUNTPOINT] using 7-zip (p7zip) or any other appropriate tool.
  **3.2.2** If [MOUNTPOINT]/EFI/boot/bootx64.efi file does  not exist, extract [MOUNTPOINT]/boot/grub/efi.img =>  <EFI.IMG>/EFI/boot/bootx64.efi using p7zip and copy it to  [MOUNTPOINT]/EFI/boot/bootx64.efi .
  **3.2.3** Move [MOUNTPOINT]/isolinux/ directory to [MOUNTPOINT]/boot/syslinux/ .
  **3.2.4** Rename [MOUNTPOINT]/boot/syslinux/isolinux.cfg to [MOUNTPOINT]/boot/syslinux/syslinux.cfg .
  **3.2.3** [GRUB_UEFI_CONFIG]=[MOUNTPOINT]/boot/grub/grub.cfg and [SYSLINUX_BIOS_CONFIG]=[MOUNTPOINT]/boot/syslinux/syslinux.cfg .
/QUOTE]

Doing this and other instruction would help confirm there is a usable(or copy of .iso efi files)efi image.

Would not seeing this
[IMG]http://i.stack.imgur.com/rL6Jh.jpg[/IMG]
 
when booting with EFI on indicate EFI installer running? ie grub the boot manager

But  would it appear the packages on iso is problem?

As hinted at in previous posts indicating my suspicion of grub hunting  for signed.efi but if can not find secure boot system drops to bios  installer!?  is this possible explanation?
When getting to this screen and dropping to command line doing `ls -l` confirms system seeing cd0,apple1 and cd0,apple2!?  I wonder why grub can not read cd or find . efi files????? on an amd64 system!!!!

---

### Post by VMC on 2013-08-17
> **Geezanansa said:**
> rEFInd can not see any usable efi bootloaders. ...If you want to boot up using the aforementioned  rEFInd, I would suggest going over to kubuntu.org fourms and ask SteveRiley how to set up booting using rEFInd. He has stated many times how he prefers rEFInd over Grub.

> **Geezanansa said:**
> [https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)  very interesting
Yes, that is interesting.

---

### Post by oldfred on 2013-08-17
There were some bugs in syslinux were renaming files solved issues. I thought those were fixed but that may be from when the issues existed? And may still apply depending on version.

Speaking of versions. What version of Ubuntu are you using. I filed this bug but they closed it do to inactivity. But another user just asked to reactivate it. 12.04.2 has a efi file name error. Should be amd64 and is just amd6 missing the 4. If you have that please add yours to the bug report. work around is use flash drive, not DVD so you can rename and then it works.

 12.04.2 incorrect file name signed efi amd6.deb
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1172065](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1172065)

---

### Post by Geezanansa on 2013-08-17
This scenario is applicable to precise quantal and raring ie >=12.04.2  I have been using 13.04 .iso the Ubuntu install on hard drive is 13.04.  I do appreciate there are few people with this hardware attempting to make use of the EFI feature.  Can not use 7zip or mount using disc image mounter in live session to mount the actual downloaded .iso which is on windows partition.  Start up disk creator sees /dev/sr0 Ubuntu 13.04 amd64 (burnt disc which is in use)

Using .iso  <=12.04.1 means a 16bit EFI partition is made at install time which needs to be copied and then the partition deleted and the copied files replaced to a 32bit EFI parttion for Ubuntu to boot using EFI on this hardware.  If trying to install using EFI to a system with an existing 32bit EFI partition then bios installer wants to run Ubuntu will not try to use 32bit EFI partition. 

My firmware wants to use DVD as only EFI device although making USB does work but is detected as hard drive so selecting hard drive device named as sony storage device from one time boot list boots what appears to be EFI mode as the picture posted describes.  Using DVD or USB media has same outcome when booting using EFI.

All this info is communicated in a much more accurate way at [http://www.rodsbooks.com/gb-hybrid-efi/](http://www.rodsbooks.com/gb-hybrid-efi/)  and related pages.

What was first flavour to claim to be EFI capable?

---

### Post by Geezanansa on 2013-08-17
I wonder how  much more grub-efi would be compatible with all machines if grub developers worked within UEFI specification.  Apparently the dependency of renaming somebody else's bootloader is a big tut tut...:(

---

### Post by oldfred on 2013-08-17
No the issue is UEFI vendors not working within UEFI spec.

       Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

---

### Post by Geezanansa on 2013-08-17
Understood.
That is the problem.

The Canonical BIOS/UEFI Requirements [link]([http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf))  is a stomper.  It does go some way to explain Ubuntu is geared for >=UEFI 2.3.1(which is the specification windows 8 demands SecureBoot to be enabled) but there is no mention of what to expect on a non Secure Boot capable system. i still would like to think it should be possible to use Ubuntu liveDVD installation media to install using EFI on a non Secure Boot  system just like Windows does!  This link also provides information regarding FirmWareTestSuite and will try probing my firmware with these tools to try and get some accurate information regarding its EFI capabilities.

This wiki [http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/) does explain the installer priority sequence and highlights there may be more that could be done to help those trying to install Ubuntu to non Secure Boot capable system.  Both the default and fallback installer do not run for me on this system with EFI on.

---

### Post by Geezanansa on 2013-08-25
> **oldfred said:**
> It seems like your older Gigabyte board just is not fully UEFI compatible. That may be why rEFInd works or helps. I think he somewhere mentioned using UEFI with BIOS as a way to test UEFI on BIOS type systems.

 [https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

The vendors of this motherboard claim it to be capable full implemetation of EFI.  Using `efisystab` when booting Ubuntu media EFI mode confirms EFI ver1.1 rev 2 which rEFInd sees as UEFI 2.1.

Regarding the Canonical link ([http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)) indicate Ubuntu is geared for UEFI 2.3.1 which the wiki at  [http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/) also indicates this is case.  Considering the fact that UEFI specification should be backward compatible with all previous versions including EFI still does not confirm the cause why no media other than Windows can actually boot and install using EFI mode on this hardware.

---

### Post by Geezanansa on 2013-09-21
Recently tried out saucy and had to check out which iso i had downloaded after noticing in BIS DVD is using mac partition table.  Definitely using amd64 Desktop .iso!  All this may be contributing why grub can not see the vmlinuz.efi files in /casper directory on DVD.  The second picture in this Ask Ubuntu question ([http://askubuntu.com/questions/298819/how-to-point-grub-to-usable-efi-vmlinuz-files](http://askubuntu.com/questions/298819/how-to-point-grub-to-usable-efi-vmlinuz-files)) highlights grub is seeing apple installers!  see the cd partitions labeled as apple!
After installing saucy (well nearly installed as i got errors) i used boot-repair to install grub-efi making sure the renaming option was unchecked.  This gave me a EFI booting saucy!  It would appear hardcoding of firmware (at least regarding which bootloaders it can use) is not the problem causing the "you need to load the kernel first" error.   More likely to be DVD using  mac partition table.  A right regal mess.  Time for dropping Ubuntu is nearing just far to many bugs and not enough answers! And am more than convinced paid support is the main income for Ubuntu project simply due to the amount of bugs.   In BIS many errors were requesting send to boot-repair by email.  Their reply was to ask for contribution highlighting the need for funds!  So much for FOSS.

---

### Post by Geezanansa on 2013-09-21
> **oldfred said:**
> No the issue is UEFI vendors not working within UEFI spec.

       Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

It is also OS writers responsibility to ensure backward compatibility.  Have installed grub-efi without renaming bootloaders which may indicate other problems or poor efi implementation either on the firmware or OS side of things.  Did this after reading  [http://www.rodsbooks.com/efi-bootloaders/bootrepair.html](http://www.rodsbooks.com/efi-bootloaders/bootrepair.html)

---

