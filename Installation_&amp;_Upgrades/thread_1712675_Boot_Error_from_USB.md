---
title: "Boot Error from USB"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by areeda on 2011-03-23
I'm not sure this is an Ubuntu problem but hopefully you people can help me out.

I built a system based on a Gigabyte GA-890GPA-UD3H, AMD Phenom II x6, 16GB RAM and 1.5TB SATA hard drive.  No CD/DVD.

I put Lucid 10.04 LTS on a USB stick and loaded it just fine it was upgraded to Maverick.  I want to test Natty and have plenty of disk space left for a Natty partition.

My problem is when I try to boot from a USB memory stick, I get a BIOS message "Loading Operating System" then "Boot Error".  No other information.

I've tried almost everything I can think of.

[LIST]
[*]multiple version of the iso.  lately I've only been using AMD64 desktop but after I get done with the "I've tried everything" post I'll try 32 bit and a server.  Oh yeah these iso's do work in Virtual Box
[*]I've used multiple memory sticks 1GB and 16GB
[*]I've tried UNetBootin and Start-up disk creator
[*]The sticks work in my laptop (well get to the try live cd or load)
[*]If I boot in Maverick md5sum confirms the files on the cd.
[*]I've tried all the bios settings I can think might have something to do with it.  The have to do with legacy USB support.
[*]I've tried creating the startup USB on my laptop and using Maverick on the system in question
[/LIST]
I'm grasping at straws, if you can think of anything else I can try I'd appreciate it.

Here's some BIOS information from dmidecode:
```
System Information
        Manufacturer: Gigabyte Technology Co., Ltd.
        Product Name: GA-890GPA-UD3H
---------
BIOS Information
        Vendor: Award Software International, Inc.
        Version: FD
        Release Date: 07/23/2010
        Address: 0xE0000
        Runtime Size: 128 kB
        ROM Size: 1024 kB
        Characteristics:
                ISA is supported
                PCI is supported
                PNP is supported
                APM is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                Boot from CD is supported
                Selectable boot is supported
                BIOS ROM is socketed
                EDD is supported
                5.25"/360 KB floppy services are supported (int 13h)
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 KB floppy services are supported (int 13h)
                3.5"/2.88 MB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                LS-120 boot is supported
                ATAPI Zip drive boot is supported
                BIOS boot specification is supported
                Targeted content distribution is supported
-------------
```I guess I could also order a DVD drive for this system.

Please feel free to comment even if you don't know how to fix it.

Joe

---

### Post by Plumtreed on 2011-03-23
Not sure how you are 'setting' up your USB drive???

On occasion I have found it necessary to remove 'old' partitions prior to install. Use 'Disk Utility' to do this.

If you are installing to the USB you can direct the positioning of Grub in step 9? by selecting 'Advanced'.

---

### Post by areeda on 2011-03-23
> **Plumtreed said:**
> Not sure how you are 'setting' up your USB drive???

On occasion I have found it necessary to remove 'old' partitions prior to install. Use 'Disk Utility' to do this.Hmmm.  I'm not sure either.
I have formatted the disk with Disk Utility and done erase disk from the Startup Disk Creator.  I've also formatted it as fat16 using makedosfs.  All of that gives me the same error.

I THINK the problem is with the master boot record and my hardware but I have no way to confirm it and no idea what to do about it.  Searching said there used to be something called install-mbr but I can't find anything like it in maverick.

> If you are installing to the USB you can direct the positioning of Grub in step 9? by selecting 'Advanced'.
I'm not sue how to install TO a USB stick.  I'm trying to install FROM a USB stick.

I am probably missing something and I have no idea what it is.  So I appreciate the discussion.

Joe

---

### Post by Plumtreed on 2011-03-23
You can do an install to a USB drive but that won't be any help to you because you won't be able to do an install from it.

It appears that you have done everything according to the book!

What brand and what size is your USB and have you tried booting to an Ubuntu OS then rebooting from that to your USB drive?(not very scientific but it has made a difference for me on a couple of occasions)

My fail safe process when using USB drives is to format in Windows and select Fat16 for under 2GB and Fat 32 for anything larger. I also try to avoid any 'persistence' when I intend to install. Again, this is more superstition than logic but I seldom run into failures any more.

---

### Post by areeda on 2011-03-23
> **Plumtreed said:**
> What brand and what size is your USB and have you tried booting to an Ubuntu OS then rebooting from that to your USB drive?(not very scientific but it has made a difference for me on a couple of occasions)
I've tried 3 different ones:

```
Device Descriptor:
  bLength                18   
  bDescriptorType         1    
  bcdUSB               2.00 
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0    
  bDeviceProtocol         0    
  bMaxPacketSize0        64   
  idVendor           0x0951 Kingston Technology
  idProduct          0x1607 DataTraveler 100
  bcdDevice            1.10 
--1GB--
```
```
Device Descriptor:
  bLength                18   
  bDescriptorType         1    
  bcdUSB               2.00 
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0    
  bDeviceProtocol         0    
  bMaxPacketSize0        64   
  idVendor           0x1307 Transcend Information, Inc. 
  idProduct          0x0163 256MB/512MB/1GB Flash Drive
---1GB--
```
```
Device Descriptor:
  bLength                18   
  bDescriptorType         1    
  bcdUSB               2.00 
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0    
  bDeviceProtocol         0    
  bMaxPacketSize0        64   
  idVendor           0x111d 
  idProduct          0x0000 
---This is a Centon DataStick Pro 16GB---
```


How can I boot from USB from inside Ubuntu?  That might work.


> My fail safe process when using USB drives is to format in Windows and select Fat16 for under 2GB and Fat 32 for anything larger. I also try to avoid any 'persistence' when I intend to install. Again, this is more superstition than logic but I seldom run into failures any more.
I have tried with and without persistence.  I did create the stick once from inside Win 7.

If I had a CD/DVD in that system I doubt that I ever booted from a USB but I swear it worked at least once.

I did order a SATA DVD that should arrive before the weekend.  I really wish I could figure out what is different.

Joe

---

### Post by oldfred on 2011-03-23
I have a gigabyte (Intel) board. It listed every USB device under the sun as bootable, but my flash drive would not boot. I then tested it in my portable & it booted so I knew it was ok. I have several drives and was changing boot order and happened to have flash plugged in and there it was. 

Try choosing which hard drive to boot not USB devices.

---

### Post by areeda on 2011-03-23
> **oldfred said:**
> I have a gigabyte (Intel) board. It listed every USB device under the sun as bootable, but my flash drive would not boot. I then tested it in my portable & it booted so I knew it was ok. I have several drives and was changing boot order and happened to have flash plugged in and there it was. 

Try choosing which hard drive to boot not USB devices.That sounds promising but I can't seem to pretend the stick is a real hard disk.

I have several options about disk controller or add in card disks, and the order in advanced bios settings.   The I have F12 to choose boot device for one time.  But either way I have to specify USB HDD or it boots from the real HDD.

But this is still interesting.  I don't remember what BIOS settings I had when it worked, it might be in there somewhere.

Joe

---

### Post by oldfred on 2011-03-23
This is what F12 shows on my system: First one is the one on the right. If I choose hard disk then I get the one on the left. The USB-HDD from the one on the right  does not work.

---

### Post by areeda on 2011-03-24
> **oldfred said:**
> This is what F12 shows on my system: First one is the one on the right. If I choose hard disk then I get the one on the left. The USB-HDD from the one on the right  does not work.
Thanks for the pictures, that helps a lot.  I get the same F12 menu but selecting HDD (so that's what that + means) does not bring up the USB drives. (See attached).

I took pictures of all the BIOS screens, thanks for the idea too obvious for me to think of it myself.  I attached some.  Do you have similar options for USB?  If so are your settings any different?

I may reset BIOS to defaults and see if I get anything different.  Also there does seem to be an update to the Bios.  I guess I should go read what it fixes.

I am waiting for Amazon to deliver a CD/DVD drive for this system but USB is more convenient, it would be nice to figure this out.  I hate it when the damn computers win a battle like this.

Thank you for spending the time Fred!

Joe

---

### Post by oldfred on 2011-03-24
I have seen different users with different configurations have issues with either unetbootin or penlinux. 

But I have learned grub2 and something like if you have a hammer everything looks like a nail, so I boot all my ISOs with grub2 and loopmount them. It is easier in my mind to just copy the ISO to the flash drive and do minor edits to my grub.cfg. I also then have several ISOs on one 4GB flash drive.

ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
HOWTO: Boot & Install Ubuntu ISO from the Grub Rescue Prompt
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by areeda on 2011-03-24
[QUOTE=oldfred;10596322 so I boot all my ISOs with grub2 and loopmount them. [/QUOTE]
Sounds promising.

Thanks for the links.

I'm off for enough reading to figure out what that means and how to do it.  Well I know how to loopmount an iso but my puny brain sees it happening too late to be part of the boot process.  Maybe after I've read those links I'll be able to ask an intelligent questions.

Oh and I looked up the BIOS upgrades available for my motherboard.  None of the changes seem to affect this and it looks like I have to install a floppy drive and build a Windows/Dos start up floppy if I want to upgrade.  Add that to the dire warnings about trashing the motherboard with no way to recover puts that option below using the CD drive and forgetting about USB.

Joe

---

### Post by oldfred on 2011-03-24
My BIOS has two ways to update. One is the windows way and the other is to floppy, flash drive or hard drive. It then reads it directly.

I have seen users use freedos on a flash drive to boot a dos. And I have seen instructions on using grub to boot freedos. Maybe time for some experimentation.

If you are in Ubuntu you install grub to the flash, create a grub.cfg and copy the ISO.

If flash is sdb and mounted as /media/verbatim

sudo grub-install --root-directory=/media/verbatim /dev/sdb

To make it easy to edit
sudo chmod 777 -R /media/verbatim /boot

Then edit/create grub.cfg

gksudo gedit /media/verbatim/boot/grub/grub.cfg
These are my entries but I used iso as folder for my iso files. And I then copy ISO files to my /boot/iso folder.

```
menuentry "Ubuntu 10.10 Maverick 64bit" {
    set isofile="/boot/iso/ubuntu-10.10-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile
    initrd (loop)/casper/initrd.lz
}


menuentry "Ubuntu 11.04 Natty 64bit" {
    set isofile="/boot/iso/natty-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

---

### Post by areeda on 2011-03-24
> **oldfred said:**
> These are my entries but I used iso as folder for my iso files. And I then copy ISO files to my /boot/iso folder.
Thanks for the info on BIOS but I think that has a low probability of fixing the boot from USB so I'd like to pursue the boot the iso through grub path.

I read the threads you pointed (most of them at least) and booted the natty iso I wanted from a partition on the hard disk.  The problem with that is that I need to unmount the partition with the iso to install to another partition on that disk.  Will that work?

So now II want to try to boot the iso from a memory stick. 

Your description above uses:

```
    set isofile="/boot/iso/ubuntu-10.10-desktop-amd64.iso"
 
    loopback loop $isofile 
```What I read and mine looks like:
```
set isofile="/iso/natty-desktop-amd64.iso"
loopback loop (hd0,3)$isofile
```If I want to change that to the USB stick, how do I specify it?  I know it's not hd1 but I can't find the proper moniker.

Any suggestions?  How do you get away without specifying the hard disk?  Can I just remove that part?

Joe

---

### Post by oldfred on 2011-03-24
It may be hd1.

What does this show?
```

sudo fdisk -lu
```or

sudo blkid

This is mine: MicroCenter 4 GB is my label shorted to fit:

/dev/sdd1: LABEL="MC4GB" UUID="E489-24AF" TYPE="vfat" 

If you have a primary partition left, you can shrink any partition (or the extended at the end) and create a new primary of just 1GB to hold the ISO. Then you can unmount the rest of the system. The issue with extended partitions is any mounted logical mounts the extended which in effect prevents any activity in the extended.

I find using grub that the drive you use to boot is always hd0. I have chainloaded to other MBRs and it gets confusing. I learned this more when I used one flash to do a full install to another flash. The grub entries  were way off and for some reason the search by UUID did not work, so I had to manually edit the grub settings to get it to boot.

Only when directly booting the flash drive (which you seem not to be able to do) was I able to not include the (hdX,Y) entry.

---

### Post by areeda on 2011-03-24
Now I see why you're closing in on 10K posts in these forums.  You a very big help to us newbies.  Thank you very much for you patience.

I think it should be hd1,1

```
Disk /dev/sdb: 16.2 GB, 16203750912 bytes
64 heads, 32 sectors/track, 15453 cylinders, total 31647951 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cda0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32     2498559     1249264    c  W95 FAT32 (LBA)
``````
joe@mj:~$ sudo blkid
/dev/sda1: UUID="c195294a-987b-4d36-9076-2f8943f81c69" TYPE="ext4" 
/dev/sda3: UUID="84667f6b-06be-48e3-97d3-0b22ee266d08" TYPE="ext4" 
/dev/sda5: UUID="c7d09fa0-d2d8-4bcf-a5a7-3033e673e0eb" TYPE="swap" 
/dev/sda6: UUID="63c5c1f2-f158-4906-90a1-d587e004f320" TYPE="ext4" 
/dev/sda7: UUID="0d1ee63d-0dc4-4ef0-9a5f-04b54bf24939" TYPE="ext4" 
/dev/sda8: UUID="b9f6a27a-d3d3-417b-ba57-8d41c65ca67d" TYPE="ext4" 
/dev/sdb1: LABEL="NATTYINSTAL" UUID="F29C-AE1C" TYPE="vfat" 

```/etc/grub.do/40_custom:
```
menuentry "Natty ISO" {
set isofile="/natty-desktop-amd64.iso"
loopback loop (hd1,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
} 

```The result is shown in the attached image. It sure seems like the BIOS is missing a driver for the USB hdd emulation.  Or I have it turned off somehow.

Also note:
```
joe@mj:~/Downloads/natty$ md5sum natty-desktop-amd64.iso /media/NATTYINSTAL/natty-desktop-amd64.iso
16168aeec2f35f56e0ae4fa8485c0d81  natty-desktop-amd64.iso
16168aeec2f35f56e0ae4fa8485c0d81  /media/NATTYINSTAL/natty-desktop-amd64.iso
```

The installer put the swap area at the end of the extended partition.  After it gets done moving it I'll try the 2nd primary partition idea and let you know.

Thanks for sticking with me, Fred.

Joe

---

### Post by areeda on 2011-03-24
Still no luck.  But I did learn that Ubuntu unlike the last time I checked windows allows multiple primary partitions.

It seems that even if I have the partitions defined and formatted the installer wants to rewrite the partition table (see attached error dialog).  So if the iso is on that hard disk it won't let me do it.  The only changes I made to the partition table was to select a primary partition to be mounted as / and one of the extended logicals as swap.

I do have a spare hard disk laying around, if the DVD doesn't come tomorrow perhaps I'll put that in.

---

### Post by oldfred on 2011-03-25
CHS error on a hard drive would say you have a setting in BIOS wrong, not sure about USB flash. That is cylinders, heads, sectors and that has not been used for years. Not since Hard Drives exceeded 8GB, I think. But has been updated several times. Everything uses LBA large block allocation. Most software still lists CHS including fdisk and others, but LBA just sets defaults for those values. The reported CHS values on flash drives are not as consistent but should not be defining the drive.

You can have 4 primary partitions with one of the four converted to an extended which is the container for many logical partitions. 

If you do not have window you can use the newer gpt standard in place of MBR (msdos) which lets you have all primary partitions - 128 or maybe more. But grub2 just started supporting it directly with 10.10. I had to add settings with 10.04. I would not change now, but just for info. And if you get over 2GiB drives, you will need gpt.

I still think it may pay to review BIOS settings. I still have not implemented AHCI (Intel) as my XP does not work. 
I have saved all these comments as different BIOS seem to use different terms. Check if any of these apply.

BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
core unlocker feature on asus m4a87td usb3 was causing the problem
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
BIOS setting, Keyboard response in grub really slow

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

Oldfred was right on, it was the SATA Native IDE setting that hosed Grub. I had to set the OnChip SATA Type to AHCI in order to boot using Grub. As for the OnChip SATA Port 4/5 Type setting it doesn't have any affect on Grub, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.

---

### Post by areeda on 2011-03-25
I will probably wipe this disk when I'm ready to switch to Natty so I'll learn about gpt before then.

I've already fooled with everything I thought might have some relationship with this but reading your list I

[LIST]
[*]Disabled internal graphics
[*]Disabled on chip SATA3 support
[*]Changed the SATA/EDE mode to AHCI
[*]Disabled firewire (nothing connected yet)
[/LIST]
It always gave me just a boot error and never listed the USB Stick as an HDD.

Attached are pictures of my bios screens I'd appreciate any comments.

I may have used a different USB although I wonder if it's got anything special these 3 don't have.  I'm doing an archaeological dig for the one I used when it worked.

Joe

---

### Post by oldfred on 2011-03-25
Because yours is AMD and mine is Intel there are differences, but also some settings are identical.

What settings do you see when you click on your hard drive. I have IDE set to auto and Access set to auto.

What is strange on my system is the first drive has CHS, LBA, Large, & Auto as choices but the other two drives only have Large & Auto. And the first two drives are identical 160GB drives.

I have seem some users say Large worked where Auto did not. But these are all hard drive settings. Other than USB Storage Function enabled, I cannot find any setting directly relating to booting USB.

---

### Post by areeda on 2011-03-25
I'll see what I can find on the hard disk settings in a bit.

My current efforts are:

[LIST]
[*]I found the USB worked before and same effect
[*]Downloading 10.04.2 to see if that one will boot.  It was a .0 or .1 that worked but I'm starting to suspect the boot loader itself.
[*]I'm reading up on PXE, looks easy enough if I had a closed network without DHCP and wanted a single boot option.  But I don't understand the security implications of turn on tftp or how to limit it to one interface.  I have DHCP running on a CentOS box. Please don't respond to PXE here as soon as I understand it well enough to ask a question I start another thread.
[*]I expect my DVD to get here today by COB.
[/LIST]
Joe

---

### Post by areeda on 2011-03-25
A bit more information:

The 10.04.2 stick failed with the same error "Boot Error" see attached.

On some reading I found the Smart Boot Manager which is supposed to use older CD drives using a floppy as the boot medium.  Didn't work of course but the interesting piece of info is that the error message changed to "SMBK error" (see attached).

This means to me that the BIOS is reading the Bootloader from the USB and it is the Bootloader that is failing.

I also have the option of Auto and Large if I select the hard drive.

Now I will look for an old version to see if it boots.

---

### Post by oldfred on 2011-03-25
Drive setting look the same as mine. Should be ok.

Yes those seem like it is trying to boot but not working. How are you creating USB flash drives?

I have used both Microcenter unbranded and Kingston flash drives without issue. Some have had problems with some flash devices and system combinations.

There were some bugs with some versions of syslinux but they normally give a syslinux error.

---

### Post by oldfred on 2011-03-25
If you have a working Ubuntu, plug in a flash that should work and run this. I want to see if the script sees the flash drive and what if reports for the MBR.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

There is also a newer version (56) being tested. Gert is busy and will not be able to finalize it for a bit but it seems to work.

Get last development version of Boot Info Script:
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

---

### Post by areeda on 2011-03-25
Here's what I got from boot_info_script055.sh I did edit it to remove the information regarding the hard disk.

I ran it on my laptop and the desktop in question with the same results (for the usb stick.

Now to see if I can highlight it like you said.  OK I see you just wanted it in [noparse]```

```[/noparse] tags.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb


sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 61.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1007 MB, 1007682048 bytes
32 heads, 61 sectors/track, 1008 cylinders, total 1968129 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             61     1,967,615     1,967,555   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sdb1        12DC-C448                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/12DC-C448         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)



=========================== sdb1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3d 00 20 00 00 00 00 00  |........=. .....|
00000020  c2 05 1e 00 80 07 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 48 c4 dc 12 20  20 20 20 20 20 20 20 20  |..)H...         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 b8 cb 0d 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 2c  7e dd ca 8f 72 75 76 ea  |~...f.>,~...ruv.|
00000120  40 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |@~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by oldfred on 2011-03-25
I do not think flash looks normal. I have used gpt for my last couple of flash drives so I cannot directly compare.

We have often seen windows have trouble booting when the boot sector does not match the results from fdisk. Nevermind, I just found an older flash drive and it has the same message of different sectors.

Your flash has syslinux in the MBR, but script does not show any boot files. Not sure if older script shows them. My download of current version shows the syslinux boot files. You also have a grub.cfg, but not the grub in the MBR.  Do you have the files it shows in /casper? Or is this the way unetbootin works. I have not used it for so long I have forgotten.

---

### Post by areeda on 2011-03-25
This is my big problem.

I don't know what these things are supposed to look like.

I'm giving up for now.  DVD-drive should get here in about an hour or two.

Joe

---

### Post by areeda on 2011-03-25
And remember this stick boots on my laptop so I do believe all necessary files are there.

To recap mostly for me since I'll get back to this.  Probably with a USB stick created by Natty.

[LIST]
[*]I've tried creating the stick different ways:
[LIST]
[*]Under Maverick with UNetbootin
[*]Under Maverick with startup disk creator
[*]Under Windows with Universal USB installer
[/LIST]
[*]All these methods boot on my laptop but give "loading operating system\n Boot Error" on my Gigabyte MB/Phenom II x6 desktop
[*]I've tried 4 different USB sticks all work on laptop none on desktop
[*]I've tried putting natty daily CD and released Maverick on the USB
[*]I use the Smart Boot Manager (for a floppy boot to install from CD) and got a different error "SBMK error" which leads me to  believe that the Bootloader is getting loaded but doesn't support the USB drives in that machine.
[*]I've twiddled every BIOS setting I can think of including "Set to Fail Safe defaults" and "Set to optimized defaults" with no change (except turning off USB support).
[*]The frustrating thing is that I have loaded 2 Ubuntu partitions on that system from USB in the past.
[/LIST]
I'm convinced that it is a bootloader incompatibility with the USB of that system.  I filed a bug report, well at least I tried.  I'm still waiting for a confirmation or a search to find it.  I'll add a link.

Joe

---

### Post by oldfred on 2011-03-25
If they work on laptop then they must be good. I cannot think of any other settings in BIOS. Sometimes they make improvements in BIOS that are not posted, but if you are getting CD/DVD then you will have an option.

---

### Post by areeda on 2011-03-25
I really appreciate your help and persistence Fred!

I've learned a lot from this exercise even if I didn't get it working

Joe

---

### Post by oldfred on 2011-03-25
You are welcome.

I hope DVD solves issue for time being, but you should be able to boot USB. I will keep on the lookout for other solutions.

---

### Post by oldfred on 2011-03-25
Someone in another thread mentioned that some USB ports let him boot and others did not.

I only by coincidence use the USB2 ports to boot as they are my front ports. What ports are you using?

lsusb is in synaptic as part of usbutils.

```
fred@fred-LucidDT:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
fred@fred-LucidDT:~$ 

```

---

### Post by areeda on 2011-03-25
Most of my testing was done with the front ports but I did make a point to try one of the USB 3 and one of the rear USB 2.  I think I have 10 available with another 6 on the motherboard with nothing plugged in.

I guess I should try all of them at least once.

lsusb produces:

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0430:0005 Sun Microsystems, Inc. Type 6 Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0764:0501 Cyber Power System, Inc. CP1500 AVR UPS
Bus 004 Device 002: ID 0430:0100 Sun Microsystems, Inc. 3-button Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by areeda on 2011-03-25
I'm not sure why my previous attempt at filing a bug report failed but it is now files as [bug # 742862](https://bugs.launchpad.net/ubuntu/+bug/742862)

---

### Post by santhony on 2011-09-25
I have this same problem with my Gigabyte Board also.. I actually have two of these Boards.. They both have the same problem...  When I first recieved this board, I RMA'd because of this, only to receive the next with the same issue...

There definetly is an issue with the Gigabyte USB hardware.... Periodically, I check around the web for a fix for this... This time I came across your Post.....

I think several Gigabyte Boards suffer from this issue... Once I read it had to do with the NEC USB chipset...

Anyways.. Let me know if anything changes, Likewise, I will do the same...

I hate burning CD/DVD's.. what a waste....

---

### Post by areeda on 2011-09-25
It's hard to blame Gibabyte or NEC because the USB works fine once you boot and it's hard to blame Ubuntu because it boots from most other USB devices.

I just wish it worked.  I did a bit of searching to see if I could find the code responsible without success, not that I'm sure I could do anything about it.  I have written boot loaders but years and years ago.

---

### Post by inspiral on 2012-02-08
> **santhony said:**
> 
I hate burning CD/DVD's.. what a waste....

I have exactly the same "boot error" problem with a brand new GA-E350N-USB3 unfortunately it's utilised in tiny case with no dvd so this isn't an option :cry:

I've voted on the bug and added a couple of comments plus I've also logged a ticket with Gigabyte.

Do you guys my any progress on find a solution in the months since you posted ?

---

### Post by inspiral on 2012-02-09
> **inspiral said:**
> I've voted on the bug and added a couple of comments plus I've also logged a ticket with Gigabyte.


I've not had a response yet but if you've got the same problems then raise a ticket, the more that do the more likely they'll look into it properly. Ticket submission is at the bottom of this page:

[http://uk.gigabyte.com/support-downloads/support-downloads.aspx](http://uk.gigabyte.com/support-downloads/support-downloads.aspx)

---

### Post by res0r9lm on 2012-06-16
I just bought a gigabyte board and ran into this problem with my usb flash drives. Too make a long story short 1 was made with "HP USB Key Boot Tool" the other 2 were made with unetbootin. The one made with the HP Tools boots but the other 2 don't. I noticed they are formatted differently. 

```
 Bus 002 Device 003: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
``````
Disk /dev/sde: 2000 MB, 2000748032 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3907711 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x006290e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63     3907710     1953824    c  W95 FAT32 (LBA)
``````
Bus 002 Device 005: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
``````
Disk /dev/sde: 2020 MB, 2020872192 bytes
63 heads, 62 sectors/track, 1010 cylinders, total 3947016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000f603

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          62     3945059     1972499    b  W95 FAT32
```

---

### Post by genoskill on 2012-09-06
Hi guys, I found a solution for this 890gpa-ud3h issue. I'm not an expert but I THINK that to make the usb boot on this motherboard the usb needs to NOT HAVE a partition table.

this is what i did:

I used palimpsest (gnome-disk-utility) to format the entire drive, and in scheme i chose "Don't partition". Then i did "Format volume" in FAT.

Then with Unetbootin I """installed""" an ubuntu based distribution that i previously downloaded. [COLOR=Red]I CHOSE /dev/sdb (because there is no partitions, i guess).[/COLOR] Also I added 1.2GB of persistency in the unetbootin menu, to suit my necessities. 

Then with clicking on any option to boot(USB-HDD, USB-CDROM, USB-FDD, USB-WHATEVER) it just booted to the Unetbootin boot menu. It worked.

pd:
```
Disk /dev/sdb: 3926 MB, 3926949888 bytes
121 heads, 62 sectors/track, 1022 cylinders, total 7669824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e87d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3223366752  3470046675   123339962   f4  SpeedStor
/dev/sdb2   ?   378192737   710426324   166116794   10  OPUS
/dev/sdb3   ?   225603442   225603451           5   74  Unknown

Partition table entries are not in disk order
```

---

### Post by zSeries on 2012-09-06
It is a BIOS problem on GigaByte mobos. I had the same problem. Eventually got GigaByte support in the UK to send me an older BIOS, F6. That worked. I don't have the mobo or BIOS details on hand. I can post them tomorrow. I also remember something about having to format the USB stick on a Windows machine to Fat16. Something is different if you format to Fat16 in Ubuntu and that is why the BIOS is giving a boot error.

---

### Post by zSeries on 2012-09-07
I have a GA-MA785GM-US2H(rev. 3.3). I used USB Creator on Ubuntu 10.04 to make the bootable USB. Originally it failed to boot with F11 BIOS, upgraded to BIOS F12 no difference. Back level to F6 and could boot OK.

Later found if I used Win7+unebootin it would boot with later BIOS.

I suspect this could be a problem with any 785 chipset mobo from gigabyte. See also [http://ubuntuforums.org/showthread.php?t=1819173](http://ubuntuforums.org/showthread.php?t=1819173).

---

