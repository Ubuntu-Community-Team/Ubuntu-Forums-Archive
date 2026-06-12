---
title: "Install of Ubuntu 10.10 for dual boot on Win7 hangs"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by Bill Grabowski on 2011-04-13
I have successfully installed Ubuntu 10.10 on two older computers, one a laptop using wubi, and the other an older Dell 8250 using an install CD with a dual boot on one drive. Now I'm trying to install Ubuntu 10.10 32 bit to my Windows 7 64 machine which has one C: drive with one partition and plenty of free space, with the goal of installing Ubuntu to a logical second partition on an external hard drive attached with a USB connection.

Unfortunately, after I boot from CD and start the install, I can't get past the install screen titled "Preparing to install Ubuntu", on which I have checked "Download updates while installing" and "Install third party software". I have three green checks for the install criteria and am connected to the internet. After I click "Forward", the spinning "busy" mouse icon continues to spin for about 20 minutes (I haven't gone longer than this) but does not progress me to the next screen. I can quit the install by clicking on "Quit".

Do I need to use the 64 bit version of Ubuntu? Any other suggestions?

---

### Post by Mark Phelps on 2011-04-13
Don't have an answer -- since you SHOULD be able to install 32-bit Ubuntu on 64-bit hardware (I've done that without problems myself).

However, a concern I have about how you're going about this is that, unless you're really careful, you'll end up isntalling GRUB 2 to your internal Win7 drive -- and that can hose up Win7 boot capability.

To be safe, before you do this, you should use the Win7 Backup feature to create and burn a Win7 repair CD.  That way, if the MBR or Win7 boot loader get damaged, you can restore them using that CD.

---

### Post by Bill Grabowski on 2011-04-13
Mark,

Good advice about the Win7 Backup/Repair CD -> created. 

You mentioned concern about how I was going about this; am I doing anything incorrectly here? As far as I know, I'm following the recommended procedure.

Bill

---

### Post by Dutch70 on 2011-04-13
It would also be a good idea to just unplug your hdd with windows on it. I have 10 OS's and I still unplug mine if I do an install. Takes about 30 seconds. ;)

I just want to make sure, you're not using an upper case letter or anything odd in your user name are you?

Just a thought, but if nothing else works, you may want to try waiting to get the updates after you install & see if it goes forward then. Could be a problem with the download site.

---

### Post by Bill Grabowski on 2011-04-13
Dutch,

I'm not getting far enough into the install to add a username. I capitalized my username on the other installs without problem.

I unchecked the get updates and third party software during install, but same problem.

I set the USB backup discs to boot before the Win 7 disc, so won't boot from USB disc.

Bill

---

### Post by Dutch70 on 2011-04-13
> I set the USB backup discs to boot before the Win 7 disc, so won't boot from USB disc.

For the life of me, I cannot figure out that statement. :P

Will it boot into a live session if you select "Try Ubuntu"? 
Is this the same cd you used for the other installs? If so it's still possible that it has become corrupted, or dirty. You may want to check it for defects again if you have already. 

If it's not the same cd, you may want to check it & the md5sum of your downloaded .iso. 
[[COLOR="Red"]https://help.ubuntu.com/community/HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

Also, what are your hardware specs? 

I'm not sure how you managed to use capital letters, as they are not allowed by default & it's a heck of a work around if you want to use them. 
It's also a common problem on these boards.
[[COLOR="Red"]http://askubuntu.com/questions/19455/using-capitals-in-my-username[/COLOR]]("http://askubuntu.com/questions/19455/using-capitals-in-my-username")

---

### Post by Bill Grabowski on 2011-04-13
Heehee. Guess that was a bit criptic. Sorry. What I meant was I put the Win 7 disc below the non-booting USB disc so it wouldn't boot to Windows. Don't know if that had a similar effect to unplugging the drive or not.

It was the same CD used to install the other Ubuntu installation, and it's clean.

I used capital letters, but they username went to all lower case anyway.

OS Name	Microsoft                Windows 7 Professional
Version	                         6.1.7600 Build 7600
System Model	                 P5K
System Type	                 x64-based PC
Processor	                 Intel(R) Core(TM)2 Quad CPU Q6600 @                            2.40GHz, 2394 Mhz, 4 Core(s), 4 Logical Processor(s)
BIOS Version/Date	         American Megatrends Inc. 0603, 7/3/2007
SMBIOS Version	                 2.4
Installed Physical Memory (RAM)	 8.00 GB
NVIDIA GeForce GTX 460, 768MB
2x Optiarc DVD RW
465 GB NTFS C: Intel SATA
WAN Miniport (SSTP)

---

### Post by Bill Grabowski on 2011-04-14
**Update**:

I decided to let the install proceed from the "Prepare to Install" screen and let it cook overnight. This morning I awoke to the next screen, "Allocate Drive Space", so whatever is happening, it's taking a *looooooonnnnnnggggg* time. I also noticed that it took about a day to defragment my hard disk, and I don't know why. 

I'm now waiting for the allocate drive space to finish. This could be a while also.

---

### Post by oldfred on 2011-04-14
Some have had issues with some BIOS settings. One user had a CD in and it went off and wanted to do filechecks on the CD. Another had BIOS saying it had a floppy but no floppy drive existed so it searched for a long time.

Random comments by others, you can review and see if any may apply.

Some issues on booting install:
BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
core unlocker feature on asus m4a87td usb3 was causing the problem
Old BIOS, new drive 137GB max boot size
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
BIOS setting, Keyboard response in grub really slow

---

### Post by Bill Grabowski on 2011-04-14
Oldfred,

Hmmm ... some of those might apply.

Bill

---

### Post by Bill Grabowski on 2011-04-14
Well, after a while I was able to install Ubuntu on the second partition of my external USB hard drive and the 8 GB swap file on the C: drive behind the primary Win7 partition. The computer is technically able to boot from the external USB drive. On reboot there is no screen asking for a dual boot to either Windows or Ubuntu. If I select the external drive to boot first, all I get is a terminal screen that says "grub recover >".

Why is there no boot option screen?

Is there a way to "fix" or activate grub?

Would it have been better to put Ubuntu in the first partition of the external USB drive?

If I remove the Ubuntu partition and swap file partition, will there be a subsequent boot problem to Windows? i.e. is grub still out there?

---

### Post by oldfred on 2011-04-14
It is often best to have all the system partitions on one drive so it is always bootable.

Grub usually installs to sda or first drive unless you use manual install and tell it then to install grub's boot loader to sdb or whatever drive you are installing to.

To see what is where. You may just need to install grub's bootloader to sdb. You can add a swap or if you have lots of memory can get by without any swap. It should boot but give an error on fstab having a partition it cannot find.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Bill Grabowski on 2011-04-14
oldfred,

That was pretty cool. Here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   956,271,999   956,271,937   7 HPFS/NTFS
/dev/sda2         956,272,638   971,896,831    15,624,194   5 Extended
/dev/sda5         956,272,640   971,896,831    15,624,192  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 251.0 GB, 250999209984 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490232832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   245,280,419   245,280,357   7 HPFS/NTFS
/dev/sdb2         245,280,481   490,223,474   244,942,994   f W95 Ext d (LBA)
/dev/sdb5         245,280,483   490,223,474   244,942,992  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A4ACF098ACF065E8                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1bdc9d3f-1d34-40e6-bfc4-539a22c1694c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0E10A99D10A98BF1                       ntfs       Backup Files and Photos       
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        aa7ffa92-b310-4aa6-b431-7a6817966707   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set aa7ffa92-b310-4aa6-b431-7a6817966707
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set aa7ffa92-b310-4aa6-b431-7a6817966707
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set aa7ffa92-b310-4aa6-b431-7a6817966707
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=aa7ffa92-b310-4aa6-b431-7a6817966707 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set aa7ffa92-b310-4aa6-b431-7a6817966707
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=aa7ffa92-b310-4aa6-b431-7a6817966707 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set aa7ffa92-b310-4aa6-b431-7a6817966707
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set aa7ffa92-b310-4aa6-b431-7a6817966707
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a4acf098acf065e8
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 0e10a99d10a98bf1
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb5       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1bdc9d3f-1d34-40e6-bfc4-539a22c1694c none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 211.6GB: boot/grub/core.img
 205.2GB: boot/grub/grub.cfg
 195.0GB: boot/initrd.img-2.6.35-28-generic-pae
 211.6GB: boot/vmlinuz-2.6.35-28-generic-pae
 195.0GB: initrd.img
 211.6GB: vmlinuz
```

Bill

---

### Post by oldfred on 2011-04-14
Boot script does not show much. Other than swap is on sda with Ubuntu on sdb. Grub's boot loader is installed in sdb's MBR and points to the correct partition sdb5. UUIDs look consistent. 

Sometimes grub has to be reinstalled. Sometimes old systems cannot boot beyond 137GB or BIOS settings on newer systems may be set to legacy IDE mode and do somewhat the same thing.

I would try reinstalling grub2's bootloader to sdb and check BIOS for IDE mode or other related mode settings. Names seem to vary by BIOS.

More comments from others:
It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another line showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> &#8220;Large&#8221;, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

It was the SATA Native IDE setting that hosed Grub. I had to set the OnChip SATA Type to AHCI in order to boot using Grub. As for the OnChip SATA Port 4/5 Type setting it doesn't have any affect on Grub, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sdb5 and want grub2 in drive sdb's MBR:
#Find linux partition, change sdb5 if not correct:
sudo fdisk -l
#confirm that linux is sdb5
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb
# After rebooting into working system
sudo update-grub

---

### Post by Bill Grabowski on 2011-04-15
Results from commands in blue.

> **oldfred said:**
> 
#Find linux partition, change sdb5 if not correct:
sudo fdisk -l
[COLOR="RoyalBlue"]This command lists Linus on /dev/sdb5[/COLOR]

#confirm that linux is sdb5
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
[COLOR="RoyalBlue"]Commands work[/COLOR]

# After rebooting into working system
sudo update-grub
[COLOR="RoyalBlue"]/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)[/COLOR]

In my BIOS, SATA can only be configured to IDE.

If I try to boot from the external hard disk, I get a grub error.

How about if I delete the volumes containing the swap files on the main drive and the Linux volume on the external, and reinstall Linux on the c: drive? Would I also have to remove grub somehow?

---

### Post by oldfred on 2011-04-15
You cannot run the update grub until you reboot. If install said it installed can you now boot the external?

Having an old grub bootloader in the external will not make any difference unless you try to boot it and it is not working.

You can do a full install in the internal. But I would highly recommend you manually partition in advance. Some of the install along side buttons are not really labeled correctly and overwrite entire drive. If you use manual install then there are no issues.

Some examples of installs and issues:
Issues on dual boot in same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by Bill Grabowski on 2011-04-15
I did a reboot before and after the grub update. No joy. Cannot boot to external.

Am now doing a manual install and partition as you suggest. 

Thanks for help. Will let you know how it goes.

---

### Post by Bill Grabowski on 2011-04-15
oldfred,

Well, I used your hints and advice and shrank the Win7 partition to make room for a 2048 MB swap and divided 30 GB between ext4 / and /home partitions which I made in the Ubuntu installer per the instructions in the hints provided in your links. All seems to have worked, and I now have grub giving me boot options, to which I am now booting into Ubuntu and downloading upgrades. 

I now have a better understanding of this process. I will continue my education on Ubuntu. Thanks again.

Bill

---

### Post by oldfred on 2011-04-15
Glad that worked. 

I always like to have a shared NTFS partition, so I do not write into a windows system partition. I learned to put Firefox & Thunderbird profiles in the shared, so when my wife wanted to use system I did not have to reboot into windows. All of a sudden we were on Ubuntu a lot with only one or two apps in WinXP.

---

### Post by Paul.E.T on 2011-04-16
> **oldfred said:**
> ....
Random comments by others, you can review and see if any may apply.

Some issues on booting install:
....

[http://ubuntuforums.org/showthread.php?t=1598419](http://ubuntuforums.org/showthread.php?t=1598419)
October 18th, 2010 	  #5

Re: 10.10 Development branch still installed?

Have you looked to see if you have /etc/motd.tail? Try removing that.  quote

How did the moth file effect the system to cause this problem ?
could be worth knowing for future ref.

---

