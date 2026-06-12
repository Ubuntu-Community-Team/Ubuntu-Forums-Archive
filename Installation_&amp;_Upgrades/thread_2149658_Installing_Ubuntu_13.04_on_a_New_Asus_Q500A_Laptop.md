---
title: "Installing Ubuntu 13.04 on a New Asus Q500A Laptop."
date: 2013-05-29
forum: Installation &amp; Upgrades
---

### Post by irv on 2013-05-29
I have heard so much about UEFI, and I wasn't sure about trying Ubuntu but I found it was easy to boot from a USB just to check to see if Ubuntu would see all my hardware. (I wanted to make sure my wifi would work).
I found that hitting the F2 key at boot up to get into the BIOS did not work. But I also found that there is a way. While in Windows 8 at the desktop pull the menu open on the right side of the screen. Select "Setting". On the bottom of the setting menu there is a hot link "Change PC Setting." This will open this window: [ATTACH=CONFIG]243242[/ATTACH]
Go to "General" on the left and scroll down to the bottom  and chose " Advance Startup "Restart Now". Then you can select to start from a USB.
When I did this it booted into the live OS on the USB stick.
Now I am on the road and not at home so I didn't want to install on my hard drive because my Internet is very slow. But I did try to install on a external SSD I had with me, but I had some issues. Because of the slow Internet It had trouble loading software. I will wait until I get home then try again. I may just install the SSD drive internally and then do a fresh install. Since doing the above I can now get into the BIOS using the F2 key to change the setting to boot into Ubuntu. 

Before doing this I plan on backing up my Windows 8 Recovery partition using a program called "ASIS Backtracker" It was a free [download]("http://support.asus.com/Download.aspx?SLanguage=en&p=3&s=480&m=ASUS%20Backtracker&os=36&ft=14&f_name=AsusBacktracker_Win8_64_VER200.zip#AsusBacktracker_Win8_64_VER200.zip"). 
When I get home I will be adding to the thread.

---

### Post by irv on 2013-05-29
Okay when I got home I installed the SSD with Ubuntu in the laptop and booted but got some error because I had Ubuntu install from my old Dell laptop. So I tried an update from 12.10 to 13.04. That didn't work either so I did a clean install of 13.04. Now the funny this is when I boot the live OS from the USB stick before doing the install it runs great and everything works. When I boot off the SSD that I installed internally it has problems. No Wifi, no mouse no touch screen. Maybe I will have to do a install of 12.04 or 12.10 and see if either of them will work.
I completely formatted the drive and will do a fresh install in a few days to see if I can get it to work. The think that gets me is, why does the live 13.04 OS off the USB stick work and when I install it on the SSD it doesn't?

---

### Post by fantab on 2013-05-30
If you are booting with UEFI then the following checklisk might offer some clues:

Have you partitioned your SSD with GPT partition table?
Have you created an 'EFI' partition as your first partition on SSD?

If your Windows8 is 64bit, booting with UEFI then the disk has to have GPT table. To boot Ubuntu in UEFI too you will need GPT partitioned SSD.
There has to be an 'EFI' partition of about 200-300MB formated with FAT32 and must have a 'boot' flag on it on every Disk, HDD and SSD. Your Win8 Disk has one if its booting in EFI.
To be able to install in EFI mode you need to boot the LiveUSB in 'EFI' mode.

My two cents...

---

### Post by irv on 2013-05-30
Okay, I am back on the road again so when I get home I will check all out with gparted on the live OS USB install stick. Then I will setup the SSD partition the way you described. 
Thanks for the info. This UEFI stuff is all new to me. Haven't had a new laptop for over 8 years now. I do have to say that old Dell I had really played well with Ubuntu. It was a Insprion 1521. Sad day when it died. I might have to see if I can get a motherboard for it. It powers on and then goes off right away. Tried two different power supplies and two different batteries.

---

### Post by irv on 2013-05-30
Okay, I am back on the road again so when I get home I will check all out with gparted on the live OS USB install stick. Then I will setup the SSD partition the way you described. 
Thanks for the info. This UEFI stuff is all new to me. Haven't had a new laptop for over 8 years now. I do have to say that old Dell I had really played well with Ubuntu. It was a Insprion 1521. Sad day when it died. I might have to see if I can get a motherboard for it. It powers on and then goes off right away. Tried two different power supplies and two different batteries.

---

### Post by irv on 2013-06-04
Everything you said sound good, but I have no idea how to do this. I am booting with UEFI in Windows 8.
I could not figure out how to partition the SSD with GPT. I am booting from a USB 2 gig with live OS and am trying to install on a external USB 160 gig SSD. When I run gparted from the live OS I see the SSD as sdc. From this point I can't figure out how to format with GPT. 
When I go to install on the external SSD I picked the boot drive to boot from the external SSD, but after installing the Ubuntu OS with the mount point see to / on the sdc it tries to boot and then give me an message, "it is taking to long to find the boot drive.
I am not trying to boot side by side with Windows 8, I want to just plugin the external SSD into the USB 3 and boot from it.
Any help will be well received.

---

### Post by fantab on 2013-06-04
In **Gparted** menu you will find '**Device**', if you click on it you get to '**create partition table**', select '**advanced**' and **GPT** or GUID Partition table. This will wipe out all your data on the SSD so if there is anything valuable then you should back it up first.

Ubuntu will not install in UEFI without GPT.

---

### Post by irv on 2013-06-06
Okay I created and GPT partition table on the SSD, but I still am getting the same error that it is taking to long to find the boot drive. I am starting to think I need to repair the grub. I believe I need to do this from the live USB but do I need to have the USB SSD plugged in so the grub can find it?
When I boot the live USB I can read the SSD and it looks good. I think I got a good install of Ubuntu 13.04.

---

### Post by fantab on 2013-06-06
Have you created an EFI partition (200-300MB) on SSD?
From your UEFI/BIOS setup make SSD your first boot device. The idea is when USB-SSD is plugged in it should boot first and you get a GRUB Menu. But when it is not then Windows will boot, without any Grub menu. 
Yes you have to have the USB SSD plugged in.

---

### Post by irv on 2013-06-07
All I have is a ext4 partition and a swap. I made a 4 gig swap so I could shrink the swap and get the 200-300MB for the EFI, but does it need to be the first partition? and how do I make a EFI? I don't remember seeing that as a choice in the format under gparted. Do I format as Fat32 and how do I set it as EFI?

---

### Post by fantab on 2013-06-07
It should preferably be the first partition, but I think it can be any partition within the first 100GB of the SSD/HDD. If its not too late then I suggest you make your first partition on SSD as EFI partition (EFI partition is ordinary partition, formatted with FAT32 with a 'boot' flag on it):

**300MB FAT32 and put a 'boot' flag on it**. You can put a 'boot' flag on it from gparted, right click on the partition ->'manage flags'->boot

---

### Post by oldfred on 2013-06-07
I bought a new SSD about a year and a half ago, but planned on a new system last summer. So I formatted drive as gpt, added both efi partition for future use and a bios_grub partition for booting with my current BIOS. Intel just released new chips so I may be building new system soon.

```
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  316MB   315MB   fat32                 boot
 2      316MB   317MB   1049kB                        bios_grub
 3      317MB   30.2GB  29.9GB  ext4         Precise
 4      30.2GB  60.0GB  29.9GB  ext4         Quantal

```

See my signature for accumulated UEFI issue and many links to more info.

---

### Post by irv on 2013-06-08
Thanks fantab and oldfred for the all the info, I will try getting the external SSD going again when I get home, am on the road again.
Maybe one more quick questing. The first time I tried to install Ubuntu on the SSD, I installed it in the laptop. It booted but it seemed to have graphic problems and few other things wrong with the install so I pulled the drive out of the laptop and have been trying to get it working this way: I l put it in a external case and plugged it into the USB port. I got a feeling that every time it tries to boot the grub is pointing to the first install (internal drive) and not the external. (sda and not sdc or sdb which ever one it is) I never changed the default location of the boot loader when I installed it. Any thought on this?

---

### Post by ubfan1 on 2013-06-08
The EFI partition does not need to be the first one, just the only one bootable.  I wouldn't put it too far into the disk, but within 4G should be OK.  Select the fat32 format, and set the bootable flag, I think that's all you need to do.  You can easily set up the EFI partition manually -- the partition contains an EFI directory, and under that directory put Boot and ubuntu directories. For removable media, and not  secure boot, you should set the /EFI/Boot/bootx64.efi file to be a copy of the UNSIGNED grubx64.efi.  The grub.cfg file (or just a stub which pulls in the copy in /boot/grub) should be in /EFI/ubuntu/grub.cfg.  You can store other files in the directories.  Usually, the /EFI/ubuntu directory is set up with a copy of shim.efi, grubx64.efi, and gcdx64.efi, and you can even add the signed copies if you want to play around with secure boot.  Just for anyone else reading who does need secure boot, the EFI setup would be: make /EFI/Boot/bootx64.efi a copy of shimx64.efi, and have a copy of the SIGNED grubx64.efi in the /EFI/Boot directory also, with the grub.cfg still in /EFI/ubuntu.

---

### Post by irv on 2013-06-10
I am going to go in a completely different direction. I just picked up a used Dell inspiron 1521 laptop off of ebay. My old dell died and I have been looking for a motherboard but this worked out even better. I got the whole laptop for the price of a motherboard so all I did was install my memory and SSD and reinstalled Ubuntu. But I went with 12.04 because 13.04 was giving me issues. Mouse and touch pad would not respond. 12.04 is working just great so I am going to stay with that for now.
Down the road I plan on installing Ubuntu on the Asus alongside Win 8, but for now I will just used my Dell. It boots in 20 seconds so when I need it I can just fire it up.

---

### Post by irv on 2013-06-14
Well, this morning I jumped in. I went ahead and installed Ubuntu 13.04 along side Windows 8. Now here is where I am now.
After completing the install and doing a reboot, it booted into Windows 8. Never got a grub menu. So I followed these steps.
While in Windows 8, I went to setting > Change PC Settings. Got the window with setting changes and selected General on the left side and Restart now on the right side. Then selected Use A device then Ubuntu.
The computer rebooted and went to the grub menu.
Now my options on the grub are as following:
Ubuntu
Advance Options for Ubuntu
Windows Recovery Environment (loader) on /dev/sda2
Window 8 (loader (on /dev/sda4)
System Setup

If I try to go into Ubuntu I get nothing. Computer just sits with a blank screen for a long time.
If I try going into Advance Options for Ubuntu I get this on the screen:
Loading Linux 3.8.0-19 generic....
Loading initial ramdisk
And then it sits at that screen and does nothing for a long time.
Finely I just reboot and it starts Windows 8 again.
I tried this several times and it does the same thing. Not sure where to go from here?

I did boot back into the the live OS and check gparted and everything looks good. I could do it again if someone needs to look at a screen shot. Oh, one other thing, I had to shut off fast boot and disabled security.

Edit: here is the screen shot of gparted. [ATTACH=CONFIG]243808[/ATTACH]

---

### Post by oldfred on 2013-06-14
That is most likely a video issue, but could be other boot parameters to configure kernel or drives to work.

What video card/chip.

 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Have you run Boot-Repair. The default Windows boot options that os-prober creates are just for BIOS and have not been fixed to be correct for UEFI. But Boot-Repair will add correct entries. See also my signature for details.

What model Asus? Several have only been able to boot K55N in BIOS mode and it works. They can install in UEFI mode but video never works. That would be a bug in the UEFI.
But many other Asus have worked.

   [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Asus UltraBook - kernel comparisons K56CA
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)
Asus Zenbook Prime UX31A (UEFI)  Blank screen resolved by turning secure boot off, many tests of Boot parameters
[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)

---

### Post by irv on 2013-06-14
I am still working on this problem. so far I ran the grub repair (which fix the grub. now I get the grub at boot up. It will boot into windows but not Ubuntu.
Next I booted into the live OS and did a
 ```
gksudo gedit /etc/default/grub in a terminal.
```
I changed the line to read 
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
But when I went to save the grub file I got this error.
[ATTACH=CONFIG]243813[/ATTACH]

Also I checked the graphic card and I have a Intel (R) Graphics 4000 in the Asus Q500A

---

### Post by oldfred on 2013-06-14
You cannot change the grub entry from a liveCD unless you do a full chroot. The sudo update-grub has to be from inside your install. Your error message is that it cannot write back to the live install.

You can use e at grub menu and scroll down to linux line and replace quiet splash with nomodeset. That is a one time change but if it does not work you can usually return to grub menu and experiment with other or both nomodeset & other boot parameters.

---

### Post by irv on 2013-06-14
That's what I was thinking. But from the linked post it didn't have a clear way of changing the grub. Not being able to get into the installed Ubuntu on the hard drive I have no way of changing it. Will I have to do another install? I am not even sure if it is a graphic issues. I get good graphics from the live OS. And running off the USB stick everything just works. I wish there were clear instructions on how to install Ubuntu on this new hardware. I could always install Ubuntu on older hardware, but this new hardware is confusing.

---

### Post by oldfred on 2013-06-14
You usually just need the temporary change to boot by editing grub entry when at menu. Screen shots in first link post #17 and just use e when on grub menu.

---

### Post by ubfan1 on 2013-06-14
I found that a Toshiba with the Intel HD4000 graphics had no video issues at all -- video just worked.  When you type "e" at the grub menu, you should see the grub commands.  Does the line starting "linux" refer to a kernel whose name ends in ".signed"?  Check the grub disks being used (the hdx,gpty) -- do they look right?  Since the Windows stuff boots, that disk hd? refers to the hard disk, I assume the next one should be the ssd with Ubuntu, but sometimes the installer gets the devices wrong, because the install media gets listed next, then the target device.  If your devices look like they are "too high" like hd2, try reducing it to hd1 and see if that boots.  First successful boot run sudo update-grub to fix up the grub.cfg file.

---

### Post by irv on 2013-06-14
OK, when I was at the grub menu I pressed "e" to edit and this is what my GNU Grub Version 2.00 13ubuntu3 looks like.
> Set params 'Ubuntu'
recordfail
	Load_Video
	gfxmode $Linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root= 'hd0, gpt6'
if [x$feature_platform_search_hint=xy]: then
search –no-floppy –fs-uuid –set= root 69d0caea-3bf6-4af2-8f56-eb3eeda8bd5e
fi
linux 		/boot/vmlinux-3.8.0-19-generic root=uuid=69d0caea-3bf6-4af2-8f56-eb3eeda8bd5e splash $vt-handoff
initrd		/boot/initrd.img-3.8.0-19-generic
So far I tried replacing the $vt-handoff with nomodeset.
This did not work.
Then I tried replacing hd0 with hd1.
This also did nothing. 
I am really not sure what I am doing here.
The thing that jumped out at me was the ext2, I thought it should be ext4 but I may be wrong.

---

### Post by ubfan1 on 2013-06-14
I think the ext2 is ok.  Now the linux line is not using the signed kernel which you need for secure boot -- I assume you need secure boot to boot windows, so Ubuntu should also use it.  Change the "linux 		/boot/vmlinux-3.8.0-19-generic" to "linux 		/boot/vmlinux-3.8.0-19-generic.efi.signed" and try that.  If you're not actually using secure boot, and can still boot windows, then check the hd0 with a simple grub "autocompletion".  Type "c" at the grub menu to get to the grub command line, type "set root=" then TAB to get the hd choices.  type "set root=(hd0," TAB to get the partition choices for hd0, and if you don't see the gpt6, your installation is on some other hd.  Try them all until you fine the one with the multiple partitions.  ESC to get back to the menu, "e" to edit and change the hd s  as necessary.

---

### Post by ubfan1 on 2013-06-14
I think the ext2 is ok.  Now the linux line is not using the signed  kernel which you need for secure boot -- I assume you need secure boot  to boot windows, so Ubuntu should also use it.  Change the "linux          /boot/vmlinux-3.8.0-19-generic" to "linux          /boot/vmlinux-3.8.0-19-generic.efi.signed" and try that.  If  you're not actually using secure boot, and can still boot windows, then  check the hd0 with a simple grub "autocompletion".  Type "c" at the grub  menu to get to the grub command line, type "set root=" then TAB to get  the hd choices.  type "set root=(hd0," TAB to get the partition choices  for hd0, and if you don't see the gpt6, your installation is on some  other hd.  Try them all until you fine the one with the multiple  partitions.  ESC to get back to the menu, "e" to edit and change the hd s   as necessary.

---

### Post by fantab on 2013-06-14
If Ubuntu LiveCD/USB is booting fine with Asus then it may not be a video issue after all. 
If your Asus Win8 is booting in EFI then, have you installed Ubuntu in EFI mode? To check, when LiveDVD/USB boots with purple screen then you have NOT, but if it boots with Black Screen with options to load Ubuntu then you HAVE booted in EFI. Please confirm this.

Post the output of the following commands from Live Ubuntu:

```
sudo fdisk -l
sudo parted -l
```

If you are sure that you have installed Ubuntu in EFI mode (even if you are not) then you may try [BOOT-REPAIR]("https://help.ubuntu.com/community/Boot-Repair") utility from Live Ubuntu. Run the 'Recommended Repair' it should fix Grub booting for ya. If not post the link which 'create BootInfo Summary' generates here.

---

### Post by oldfred on 2013-06-14
Someone with a different Asus posted this. It think it needed both parameters and monitor setting must be your monitor's size, not example shown below.

 Asus i3 with Intel graphics, 
"acpi_osi=Linux"
"video=1280x1024-24@75" or whatever native resolution is

ext2 is correct as that is the one insmod for the entire ext2, ext3 & ext4 family.
hd0 is correct if you are booting from the same drive.

---

### Post by irv on 2013-06-15
Let me explain everything I have tried so far.
I did what ubfan1 posted. The list of hd0 partitions were gpt1 through 7. I tried them all. I did add the efi.signed to the linux /boot but got an error because I have security turned off in the BIOS. Win8 is booting with out it being turned on so this should not be a problem.
OK, fantab I am getting the black screen from the live OS and am booting EFI. Here is the output from fdisk and parted. 
> ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x01a8a7c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 1998 MB, 1998585344 bytes
4 heads, 16 sectors/track, 60991 cylinders, total 3903487 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          16     3903486     1951735+   b  W95 FAT32
ubuntu@ubuntu:~$ 


> ubuntu@ubuntu:~$ sudo parted -l
Model: ATA HGST HTS541075A9 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  316MB   315MB   fat32           EFI system partition          boot
 2      316MB   1259MB  944MB   ntfs            Basic data partition          hidden, diag
 3      1259MB  1394MB  134MB                   Microsoft reserved partition  msftres
 4      1394MB  409GB   408GB   ntfs            Basic data partition
 6      409GB   720GB   311GB   ext4
 7      720GB   729GB   8475MB  linux-swap(v1)
 5      729GB   750GB   21.5GB  ntfs            Basic data partition          hidden, diag


Model: Best Buy Geek Squad U3 (scsi)
Disk /dev/sdb: 1999MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      8192B  1999MB  1999MB  primary  fat32        boot


ubuntu@ubuntu:~$ 


Oldfred the Asus Q500A is a laptop with a 15.6 screen and the video is 1920x1080.
Looking at what you posted from the other thread, should I try added my video size?

As I post this I am doing it from the live OS which is running at this video size and working well.

---

### Post by oldfred on 2013-06-15
I would try entering your video as a boot parameter. 

Some other to try or it may need combinations.
 Intel HD4000
[http://communities.intel.com/thread/34221](http://communities.intel.com/thread/34221)
[http://ubuntuforums.org/showthread.php?t=2089640](http://ubuntuforums.org/showthread.php?t=2089640)
[http://ubuntuforums.org/showthread.php?t=2126191](http://ubuntuforums.org/showthread.php?t=2126191)
Also one used nolapic.
[http://ubuntuforums.org/showthread.php?t=2133816](http://ubuntuforums.org/showthread.php?t=2133816)
GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux quiet splash"

---

### Post by irv on 2013-06-15
After beating my head against the wall, I thought I would try this. I installed Ubuntu 12.04 and replaced 13.04. and it now boots into Ubuntu but the only problem I have now is it doesn't boot into windows. I am going to run a repair on the grub and see if this helps. Will post again when I am done.

EDIT: After running the grub repair I can now boot into 12.04 and win8. I am going to try the install of 13.04 again and see what happens. The reason I want 13.04 is the touch screen is not working in 12.04. Will be back to let all know whats going on.

---

### Post by irv on 2013-06-15
I started the install of 13.04 and chose the upgrade. I was thinking it might not change the grub or boot partition. but here is what I got:
[ATTACH=CONFIG]243838[/ATTACH]
I chose the "continue" then got a message
> The attempt to mount a file system with type vfat in scsi(0,0,0), partition (sda) at /boot/  efi failed.
I continued anyway hopeing that the install would complet and not touch the boot partition or the grub.
It is deleting file that are not needed in 13.04 right now and I am waiting for the install to finish.

---

### Post by ubfan1 on 2013-06-15
I'd suggest backing up the entire working EFI partition at this point.  The partition should be mounted at /boot/efi , and you can copy the files to a  thumbdrive.  I think the 12.04 install puts the entire grub.cfg into the EFI/ubuntu directory, but the 13.04 just puts in a stub which includes the grub.cfg from the usual /boot/grub location.  With the stub in place, the normal kernel updates will be picked up by the efi boot.

---

### Post by irv on 2013-06-15
This has really been a headache. I ended up with not being able to get into either Ubuntu or Windows. Lucking I had a restore for windows on a USB so I just got done setting my system back to factory. But I notice that I still have the Ubuntu partitions. I plan on booting the Live OS and running gparted and deleting it and growing the windows partition again. I am getting to the point where I am just going to use the Live OS if I need to run Ubuntu and forget about installing it on this machine. Maybe I will wait for the next release and see if it plays better with the new hardware.

---

### Post by oldfred on 2013-06-15
Are you able to mount the efi partition. Grub has to be able to install its files into it.

Some system have a issue with the efi partition. Not sure if corruption or somehow they have locked it. The main work around has been to fully back it up, delete it, and then recreate a new FAT32 partition with boot flag and restore all the efi files & folders.

 grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)
cannot mount /sys/firmware/efi/efivars on boot - 13.04 kernel issue
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1146868](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1146868)
Some find chkdsk on efi partition helps, others backup, reformat and restore as current work arounds.

---

### Post by irv on 2013-06-15
> **oldfred said:**
> Are you able to mount the efi partition. Grub has to be able to install its files into it.

Some system have a issue with the efi partition. Not sure if corruption or somehow they have locked it. The main work around has been to fully back it up, delete it, and then recreate a new FAT32 partition with boot flag and restore all the efi files & folders.

 grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)
cannot mount /sys/firmware/efi/efivars on boot - 13.04 kernel issue
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1146868](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1146868)
Some find chkdsk on efi partition helps, others backup, reformat and restore as current work arounds.

Oldfred thanks for all the help on this one but I need to put it to rest for awhile. I may come back to this at a later date, but right now I am trying to get all my programs and date back in windows. This may take me awhile. Right now windows is doing some updates seeing I had to start from scratch. I also deleted the Ubuntu partition and expanded the Windows partition for now. I feel there are some really issues with 13.04 install on new hardware. Also I might have to download and create a new USB because it won't even boot any more or maybe it is just a setting in the BIOS.
Again thanks for the help.

---

