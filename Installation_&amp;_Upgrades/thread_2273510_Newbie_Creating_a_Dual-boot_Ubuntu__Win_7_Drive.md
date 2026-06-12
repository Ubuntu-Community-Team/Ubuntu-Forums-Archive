---
title: "Newbie Creating a Dual-boot Ubuntu / Win 7 Drive"
date: 2015-04-13
forum: Installation &amp; Upgrades
---

### Post by Tom_Daly on 2015-04-13
I'm getting a new machine setup and wanted to play with Linux and also make it a dual boot to Windows 7.  Single 3 TB HDD system with a single DVD drive and 16 GB of RAM.  This is an Intel, UEFI based Mobo.

I think I messed up my initial install somehow but that's OK; this is a new computer and I am more than happy blowing everything out and starting over.  When I finish doing the Ubuntu install (64-bit 14.04.2) from a DVD and reboot the PC does not find any OS on the HDD.  I think I misread on the first pass and selected to install it parallel to the existing OS but unfortunately there wasn't any OS installed.  Anyway, I did the Windows 7 install and it boots fine.  So I tried to install Ubuntu fresh deleting all the partitions and when complete the system still sees no OS on the HDD.

I'm not completely up to date on all the changes in file systems etc. so I'm seeking guidance for the best way to format the HDD and get it setup for optimal performance.  The main focus on the computer will be Linux (I need to run a fairly heavyweight application for work) but I want to have Win7 available as at times it will be useful.

I'll keep banging on it and trolling threads for ideas but if anyone cares to lend their experience it would be very helpful.

Thanks!

-Tom

---

### Post by oldfred on 2015-04-13
Since drive is 3TB, you must use gpt partitioning. 
And then you have to install Windows in UEFI boot mode. Most Windows 7 installers default to BIOS mode and have to be copied to a flash drive & updated to make them work for UEFI. Did you install Windows in UEFI mode?

If you have an efi partition and the reserved partition then you are in UEFI mode. If you just have a 100MB boot partition and the main NTFS, you are in BIOS mode.
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

I usually partition in advance and then use Something Else. But have not had Windows on same drive, nor with UEFI.
      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Tom_Daly on 2015-04-13
Thank you very much for taking the time out to provide some guidance.  It appears I did not install W7 in UEFI mode as I have a 100 MB partition and 548.33 GB partition that are both NTFS.  I don't recall seeing any option to do so but I followed the install tool like a lemming.

Not much has been done to the W7 install and I won't weep over redoing it.  I see that you say "[COLOR=#000000]I usually partition in advance and then use Something Else. But have not had Windows on same drive, nor with UEFI."

[/COLOR]Would you recommend I boot the machine from the Ubuntu install DVD and partition from it, then boot from it again and use "something else" carefully following the guidance in the links you have sent?  Is there a better way to partition the drive via gtp?  I'm getting better acquainted with gpt and its options and tools as I type.

One other thing I take from that quote; is it a bad idea to try and have both of these OS on the one drive?  I understand some things "should" work but just because you can does not always mean you should.  The Linux build is what I need, W7 is nice flexibility for this machine.  I have a small case for portability so one HDD is all I get unless I spend money on M.2 but that's a bit more than I want to spend right now.

Thanks so much for taking the time out to respond to me.  This is a good learning experience after a long hiatus from really digging into machines at this level.

-Tom

---

### Post by oldfred on 2015-04-13
Windows 7 should be better than Windows 8 with its secure boot and always on hibernation or fast startup settings.

I would still suggest installing Windows 7 first if you want both on one drive. If thinking of another drive then that is a better alternative, but you still should install Windows first on the first drive. 

You do have to have gpt to be able to use entire 3TB. MBR was designed 35 or more years ago and has a limit of 2TiB or 2.2TB. Back then TB sized drives were unheard of even for larger systems.

       I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Windows does have its own partition requirements that are different than BIOS install, links were above, but if you install it first then it will create its own partitions. Then use Windows to shrink the NTFS partition, do not turn on hibernation and reboot immediately so it can run chkdsk to update to its new smaller size.

      
 Convert Windows 7, 8 or 8.1  BIOS to UEFI - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)

---

### Post by Tom_Daly on 2015-04-14
So looking through everything I've booted my computer from the Ubuntu DVD under "Try Linux" and I'm moving the gparted util onto a flash drive.  From there I will make the following partitions as a GPT drive:
300 MB efi - FAT32
25 GB /root - ext4
32 GB Swap - swap
1 TB /home - ext32
Leave the rest for Win7 unformatted

I'll install Ubuntu onto this drive and if it successfully boots I'll then install Win7 in parallel with Ubuntu.  I'll figure out how to do that aspect of the install elsewhere.  I'll let you know how I fare!

Thanks again!

-Tom

---

### Post by Tom_Daly on 2015-04-14
Some things I've noticed.  I got into gparted by booting m the CD I created from the ISO.  It didn't have the option for an EFI partition but I made a 500 MB FAT32 at the start of the drive, followed with 50 GB of / as ext4, 36 GB swap and 1 TB of  /home as ext4 leaving lots left over.  I applied, gparted did its thing.  I saw a note here:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

That said I don't need to set a mounting point of the EFI partition that the installer will do it automatically.  Mine didn't perhaps that was the mistake leaving off the /boot/efi. 

Then I booted from the Ubuntu DVD, did a "something else" install.  I saw none of the partitions I'd done before so went about recreating them. The installed also lacks any option for an EFI partition but I just left FAT32 space again.  When I went to proceed and the installer cautioned me to use a BIOSGRUB partition upfront.  So I wacked everything and did that at 500 MB and recreated the whole scheme.  Install proceeded and appeared happy.  I do have a wired connection to the network for the install so I should be getting the latest patches, etc.

Upon reboot the UEFI system cannot find an OS.  <<BANGING HEAD HERE>>  At least when I go back into the installer I see my previous partitioning work.

I've gone into my boot menu again and again and it says UEFI all over, no BIOS mentions.  The board is an Asus Z97M, socket 1150 with a Haswell processor.  It seems the software thinks it is in a BIOS system.

I read all of the material oldfred was kind enough to share and wonder where I am going wrong.  For what passes as fun I am installing Ubuntu now with the "erase disk and install" option.  If that doesn't boot I'm at a loss.  Perhaps I should upgrade my UEFI.  I almost said my BIOS...

So if anyone has any thoughts I am open!

---

### Post by Tom_Daly on 2015-04-14
Nope, erasing the disk and dedicating the entire disk to Ubuntu also doesn't boot.  I'm pretty sure I'd already tried that but now I know for certain.  

I guess I'll install Win7 and then try to add Ubuntu to that.  I haven't tried that.  I cannot get Ubuntu to boot from this HDD so far.

---

### Post by Tom_Daly on 2015-04-14
And now as I review all of this I see this is what oldfred recommended.  I guess I lost that among reviewing all the links.

---

### Post by Tom_Daly on 2015-04-14
Ah yes I did try and install Win7 first, now I remember!  When I do that Ubuntu does not see an existing OS.  When I started my Win7 install it could not read or use the GPT partitions so it whacked them. I tried the advanced modes in Win7 but they were light on detail.  I did leave a lot of unused space for Ununto but it does not see any partitions just bare drive.  Ironically when I FIRST installed Ubuntu and there was no OS present (the very first anything to be installed) it DID detect an OS (that wasn't there) and I foolishly said install alongside the existing OS, thinking that would leave room for Win7.

It appears that I cannot install both Win7 and Ubuntu on this HDD nor can I have a stand alone Ubuntu install.  I installed every way shape and form.  I never have seen an option for an EFI partition and I suspect that is the issue.  I used the latest parted but no dice there either.  I'm really out of ideas.  Open to suggestions.

---

### Post by oldfred on 2015-04-14
If you did not get a partition flagged as the efi partition, were partition still MBR(msdos)?

And Windows default is BIOS with MBR, you have to modify it on a flash drive as links above. Never done it so do not know more than links.

And if one is BIOS and  other UEFI you have issues.
Post this from Ubuntu live installer in terminal mode.
sudo parted -l

       I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

And I add both an efi partition and a bios_grub to all new drives, but that was more that old system was BIOS only, and I expected newer system to be UEFI. And now with new UEFI system I am not using BIOS boot.

Also if you let Windows convert drive from gpt to MBR, it will do it incorrectly and you have even more issues. It leaves the backup gpt partition table, so then Linux tools see both MBR & gpt and assume  you must erase drive to fix mixed partitioning.

How you boot installer for both Windows & Ubuntu is then how it installs. And with a gpt drive, you must boot both Windows & Ubuntu in UEFI mode.

---

### Post by Tom_Daly on 2015-04-14
Thanks for your patience!

When I was in gparted there was no mention or EFI or GPT, I'll look again.  Also, the Ubuntu installer didn't see any of the partitions I made, applied and watched gparted work.  Ubuntu just saw a bare drive.  I'm in a bit of a catch-22; I need to learn Ubuntu but cannot get it to work. I have not the background to send screenshots from gparted, etc. when I boot from that disk.

For the command the output is:
ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? n                                                                 

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: ASUS BC-12B1ST b (scsi)
Disk /dev/sr0: 1044MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac

Number  Start   End     Size    File system  Name   Flags
 1      8192B   24.6kB  16.4kB               Apple
 2      42.3MB  51.8MB  9568kB               EFI


ubuntu@ubuntu:~$ ^C

Of course bear in mind this is post Win7 install (where I am now) so probably not of much use.  I don't know where 'Apple' is coming from!  There is nothing Apple involved

Win7 installer also knew nothing of EFI and told me it couldn't read my GPT partitions.  That makes sense as I don't have th EFI.  I'm surprised the Ubuntu does not seem to be able to partition the drive though.  I'm not backing anything up as I have nothing to save and can nuke this as I want right now.  

I'll dig through those threads again and try to find how to set EFI and take a few more passes with gparted.

---

### Post by oldfred on 2015-04-14
With gparted you select gpt first thing. 
  Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

As you cannot easily change. And usually changing erases drive, although there are some tools that will convert from gpt to MBR or vice versa, but lots of rules and not easy.

And again how you boot installer is how it installs, both Windows & Ubuntu. With Win7 you must convert installer to UEFI on a flash drive, default is BIOS/MBR.

The Mac is your DVD, and some tools are making what looks like two partitions.  But first partition has misc or random data. DVDs normally do not have any partitions, so it may just be parted trying to convert random data to a partition table. 
I only have used a flash drive in recent history as in the past I used to burn a lot of 'coasters' or bad burns and they only are good to use as a coaster.

---

### Post by Tom_Daly on 2015-04-14
My notes on my next pass.  Don't read unless you want the painful details of how NOT to do this.  Spoiler alert; machine still doesn't boot.  The mobo cannot find an OS.  Now I am fairly certain the issue is the install media being setup from a Win7 BIOS platform is just malformed for this UEFI platform.  I need to create an UEFI DVD from that platform or perhaps a USB.

When I enter gparted, which I am entering from a bootable CD, I see the note "*Boot menu for BIOS machine" in the menu where I launch the Debian gparted seems to run in.  It is gparted 0.21.0-1-i586.  This makes me wonder that although my mobo says UEFI all over perhaps it emulates BIOS?  I see it has CSM, compatability service mode.  I'm just wondering if I'm barking up the wrong tree.

In gparted (I enter the default settings), I select the partition pull-down menu and "create a new partition table" and select the partion table as gpt.  The drive is seen as unallocated. I hit the new button and set a 550 MiB partition size with 1 MiB free preceding it (default), make it FAT32, primary with a label of /dev/efi/.  I cannot set the boot flag now but will do it after I apply the partition.  I leave nothing free following the partition, on this or the following partitions.  I then do a 50000 MiB ext4 partition with no preceding free MiB (nor on the following do I) and give it a label "/".  Then it gets 36000 MiB of linux-swap allow a label of "swap". Last an ext4 of 100000 MiB with a label "/home."  I still can't manage flags so I hit "apply" and gparted does its thing.  I see on the intended /dev/efi it set the flag msft-data automatically. When I set the boot flag it takes off the msft-data flag and also flags esp.  So now boot and esp are flagged.  I see no esp is the flag but I think that's OK.  Truthfully, I noticed the note on flagging the partition as efi after I rebooted so that is recollection, such as I can manage.

Sorry for the tedious detail but I suspect a small mistake is killing me.  I think this SHOULD, a) kill everything on the drive which is fine because I'm tempted to do something violent to it and b) have this drive in the state Ubuntu wants.

I shut the system down and rebooted with my Ubuntu install DVD which as I read above may be suspect if I made it wrong.  For now I'll trust it.

The installer detects no existing operating systems.  I enter "something else" and it sees my sda1, sda2, to sda4.  Progress! I make sda1 the place for the bootloader.  Now I double click sda1 (efi) and see the installer says this is marked as 'don't use.'  I also see no efi/esp/boot option and I do see a 'BIOS boot area.'  I'm beginning to suspect this is a BIOS computer OR my DVD boots as one.  I did burn the iso from another Wim7 platform.  I aborted the install and went back to gparted, rebooting to that CD. I took off the boot and esp flags from sda1 and flagged bios-grub. After getting back into the installer I realize the BIOS-Grub is too big but I'll risk it.  I do manually set the sda2 to / and sda4 to /home and set them to format. sda1 (grub-BIOS) and sd3 (swap) were set ok.  I'm not sure if I should set sdax to the boot device so I just left it as the whole drive.  I changed my location on the time zone page to New Jersey instead of New York.  The install has begun...

Forgive my verbosity (if anyone has made it this far) but at this point I'm just putting all my notes here. I will make this machine run and figure this out. :)  Perhaps someone else struggling will find value in this.

OK, same result.  The mobo cannot find an OS.  Now I am fairly certain the issue is the install media being setup from a Win7 BIOS platform is just malformed.  I need to create an UEFI DVD from that platform or perhaps a USB.  I'll need a bigger USB for Win7 and may yet get my dual boot.

---

### Post by oldfred on 2015-04-15
The labels are for reference. I do label partitions, but that is not the mount point nor the install location.
I normally use gparted on the Ubuntu live installer, but have gparted ISO also.

How you boot install media ( I did mention this once or twice) is how it installs.
If you boot installer  in CSM/BIOS mode it installs in BIOS boot mode. And if gpt partitioned it needs a tiny 1 or 2 MB unformatted partition with the bios_grub flag.
If you boot installer flash drive or DVD in UEFI mode, then it installs in UEFI boot mode and UEFI must be set as boot option in UEFI/CSM.

ESP is the official name, installs now seem to be using it. Many of us just have called it efi.
ESP - Efi System Partition

The ESP partition is not where you install grub when installing. You always specify drive or sda. With UEFI it knows that the efi grub files go into the efi partition. And with BIOS the initial boot part of grub is installed into the protective MBR (if gpt) and more grub (core.img) is in the bios_grub partition. If drive is MBR, grub goes into MBR, and core.img is in sectors just after MBR.
With all installs other parts of grub including menu & scripts are in various / (root) folders.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Your UEFI boot menu will show a flash drive twice. Usually one is clearly UEFI & name/label of flash drive. The other is just the name of the flash drive and will be BIOS boot.

Toshiba example is a Toshiba flash drive with two entries in UEFI boot. One UEFI and one just Toshiba.

---

### Post by Tom_Daly on 2015-04-15
Yes, you did mention I need to create a UEFI boot USB for Win7.  I've been drinking from a fire-hose and missed that, my mistake.

So, now that I've seen the error of my ways I've used burnaware_free to create an osi from my Win7 DVD and then Rufus to create a bootable USB as UEFI.  This needed to be done on my BIOS based machine that functions so hopefully that is OK, I followed the instructions carefully.  In my UEFI settings I've disabled CSM.  In this state the computer will not run the Win7 installer.  I tried my gparted CD and it boots from that.  I wiped all the partitions from the drive (give Win7 a clean disk hopefully) not that I had any hope that would help but I gave it a spin.  Still system just boots to UEFI menu.  So I went back to CSM in the UEFI and enabled it but set PXE OpROM policy and Storage OpROM policy to UEFI only.  Now the Win7 disk launches but the installer acts like this is a BIOS system; 100 MB partition right up front.


I think I need to change my approach.  Forget Win7, that was a nice to have feature but not critical.  I need Ubuntu to work.  So now I'll redo what I did last night but boot gparted into UEFI with CSM disabled.

So, I booted with CSM off in gparted CD and I see it looks different.  It no longer says BIOS mode.  That's a start.  I formatted as follows:
/dev/sda1 - FAT32 - flag boot and esp - 300 MiB - I cannot name a label / mounting point here, no option
/dev/sda2 - ext4 - 50000 MiB - Label "/"
/dev/sda3 - linux-swap - 36000 MiB - Label "swap"
/dev/sda4 - ext4 - forgot the exact size but 1.2 TiB - Label "/home"
lots of unused space

Boot to Ubuntu installer.  Again, it looks different with CSM disabled.  I go into try linux as I saw it mentioned somewhere this was a better approach.  Then launch install Ubuntu.  Something else and I see none of the changes gparted made. That does not make me hopeful.  I create partitions as follows:
/dev/sda1 - FAT32 - EFI Boot sector flag - 298 MB - no mount point set or can be set
/dev/sda2 - ext4 - 50000 MB - mount point "/"
/dev/sda3 - swap - 36000 MB - no point set or can be set
/dev/sda4 - ext4 - ~140000 MB - mount point "/home"

Set boot device to /dev/sda1

/dev/sda2 and /dev/sda4 are clicked for format, I cannot click for the others so hopefully no worry.

Run Install.  The moment of truth... ***IT BOOTS***

OK.  So first off oldfred, many, MANY thanks for your guidance and patience as well to all of the kind contributors who's knowledge you directed me to.  In conclusion the trick to getting just Ubuntu to load properly in retrospect was disabling CSM.  The iso for Ubuntu install I burned onto a DVD under Win7 DID boot as did gparted.  However the Win7 UEFI iso on USB did not with CSM off and with it on treated the system as a BIOS system.  Likely I made some mistake there although I was careful.

I have not gotten a dual boot to work.. yet.  I may iso this Ubuntu build and try and load Win7 on top of Ubuntu or, create a Win7 iso for a bootable USB with a linux tool on the now completely UEFI system with CSM disabled.  I'll also try to nuke this (having isos on hand for both Win7 and Ubuntu) and start with the Win7 install IF I can get the USB to boot with CSM disabled.  Perhaps creating it from Ubunto on an UEFI system will do the trick.

Now onto the task of loading the application that required all of this although it was certainly educational.  I don't want to mark this as solved as the subject will lead folks to believe this will get dual boot to work as is not yet the case.  I will update with my progress when I can return to this.

Thanks again!

---

### Post by oldfred on 2015-04-15
Trying to create Windows installers from Ubuntu is very difficult. Many posts about how to do it and few successes. 
But for Windows 7 to be UEFI, it must be a flash drive so you can move or create the /efi folder with some UEFI boot files or BCD? Never done it.

You still should set boot as sda not sda1, but with UEFI it seems to only correctly install boot files to the ESP - EFI System Partition.
When you create partitions in advance it seems to auto find swap, and efi partitions. Your fstab will show the mount of those partitions also if correctly installed.
cat /etc/fstab

I export all applications I have installed as part of my rsync backup. Then I can use that file to install all apps automatically on a new install or a repair.

If you partition in advance for Windows see the link above for what it expects in the way of partitions, order on drive is also important. It will also use the same efi partition, as you can only have one.

---

