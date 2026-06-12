---
title: "[SOLVED] How to do a double boot/single hdd system  and have grub manage Windows XP b"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by benkyoto on 2007-08-16
I have to apologize in advance if I say things that are utterly noobish, but here we go.

A* Recently built a new computer
 -Gigabyte motherboard
 -AMD Athlon 64 3500+ processor
 -Nvidia 6600 graphics card
- 1gb DDR2
- 250 Gb HDD

B* I made this mostly from parts that were in my previous desktop computer when upgrading (save the MB), and those parts were working just fine in the previous machine.

C* I want to make this a double boot system with Windows XP and Ubuntu sharing the same HDD.

D* When I installed Windows XP, I booted from the install CD-ROM and got through the text part of the installer without a hitch. Rebooted after copying the system files. The BIOS boot sequence went normally until "Verifying DMI pool data", after which the computer would go into an infinite reboot loop (go again to "Verify DMI pool data" and then reboot again when it's supposed to start booting the OS, and again, and again).

E* Tried switching  the pieces of hardware that I thought if faulty might have caused the problem  (memory, HDD), but the best I got was the computer freezing instead of rebooting after displaying the "Verifying DMI pool data" message. Only parts I haven't ruled out as faulty are the MB (possible) and the CPU (unlikely).

F* Enough with Windows, I thought, and I installed Ubuntu. It boots and runs perfectly, which is puzzling since I assumed that no other OS would work if what I had was a hardware problem. Ubuntu... just... works. But unfortunately I need XP too. So what I did is partition the HDD in the following way during the install process to make room for the ugly guy.
 1-FAT32 partition (125000Mb)
 2-ext3 boot partition (4096Mb)
 3-swap partition (4096Mb)
 4-ext3 linux partition (the rest  119***something Mb)

G* When I finished installing Ubuntu, I tried to install XP into the FAT32 partition. The windows installer overwrote/broke grub and I found myself again in the "Verifying DMI pool data" conundrum as the XP loader tries to kick in.

H* I tried to install Ubuntu once more on top of this. Everything went smoothly (apparently) and the grub installer seemed to recognize the presence of XP in the system.

I* After I concluded the Ubuntu installation for the second time and rebooted, grub kicked in and I could get into Ubuntu again. But when I restarted once more and tried Windows XP from the grub boot menu, I got a "could not find NTLDR. Press any key to restart" error. I assume, then, that grub overwrote it, leaving me with an XP that won't start.

J* I'd like to keep grub as the main boot manager since the alternative sends the computer on crash course. How can I restore the Windows XP loader without breaking grub?

NOTE: I already checked several support sites and did most of what they suggest: swapping hard drives, clearing the CMOS and redetecting all storage devices, updating BIOS, etc., to no avail.
I am pretty much at the end of my knowledge here, so any suggestions (either to have grub manage the boot sequence of both OS's or to troubleshoot my hardware further) will be greatly appreciated

---

### Post by jnorthr on 2007-08-16
Just a thought about ur problems : have a look here: [http://www.computerhope.com/issues/ch000474.htm](http://www.computerhope.com/issues/ch000474.htm) it may help solve the dmi issues first before moving on.

---

### Post by logos34 on 2007-08-16
Look in C: (hda1) for 'ntldr' and 'boot.ini' files.  Post the latter if you could.

The only other thing you might consider is reinstalling xp after reformtting it as NTFS.  Not sure if it will help but it is a better filesystem and you can write to it if you use a special linux driver (ntfs-3g)

---

### Post by benkyoto on 2007-08-16
still struggling here... Ubuntu boots fine but XP won't start. NTLDR is present in the windows partition, so why do i get the NTLDR not found thing when I select XP from Grub. Help appreciated. See the info below.

-------------------------------

**dump from sudo fdisk -l**


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15197   122069871    b  W95 FAT32
/dev/sda2           15198       15695     4000185   83  Linux
/dev/sda3           15696       16193     4000185   82  Linux swap / Solaris
/dev/sda4           16194       30401   114125760   83  Linux


--------------------------------

**/windows/boot.ini**

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)¥WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)¥WINDOWS="Microsoft Windows XP Professional" /fastdetect

C:¥ = "&#12489;&#12521;&#12452;&#12502; C &#19978;&#12398;&#35672;&#21029;&#12391;&#12365;&#12394;&#12356;&#12458;&#12506;&#12524;&#12540;&#12486;&#12451;&#12531;&#12464; &#12471;&#12473;&#12486;&#12512;"



---------------------------------
**/boot/grub/menu.lst **

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=41bec675-0204-4475-a0b5-695fe401af84 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=41bec675-0204-4475-a0b5-695fe401af84 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=41bec675-0204-4475-a0b5-695fe401af84 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by logos34 on 2007-08-17
Your files look correct.  Maybe windows is not set or being correctly detected as active partition despite the boot flag and what menu.lst entry says. Also, make sure the hard disk is first in the BIOS device boot order, ahead of removable/floppy and cdrom drives.

I'd first run a filesystem check with repair option on the fat32 partition.  Boot frm the XP install CD, hit R for recovery console and then for C: drive/drive 1 enter

**chkdsk /r**

You might want to look through this link:
[http://tinyempire.com/notes/ntldrismissing.htm#What_if_my_backup_system_is_Linux_or_another_alt_OS?](http://tinyempire.com/notes/ntldrismissing.htm#What_if_my_backup_system_is_Linux_or_another_alt_OS?)

I'd try the suggestions there next.  So, to make a boot floppy, you'll download the **xpnt4lix.zip** file for linux, extract it and write it to a formatted diskette just as it says:

**sudo dd if=xpnt4lix.img of=/dev/fd0**

Or if making a boot CD, download the 'FIXNTLDR ISO image for Windows XP' zip file and unpack it.  Right-click on the extracted image **fixntldr.iso** and write to disc.  

If that doesn't solve the problem, try booting into the recovery console on the XP install CD and [copying ntldr and ntdetect.com files to windows partition, and then run 'fixboot']("http://support.microsoft.com/?kbid=315261").  (If it overwrites Grub, you can easily [restore it from the ubuntu CD]("http://ubuntuforums.org/showthread.php?t=224351")).

Or use [Bcupdate2.exe]("http://support.microsoft.com/kb/320397/en-us") (you'll have to google for the download/instructions)

---

### Post by benkyoto on 2007-08-17
Okay, fixed the problem, only to break it a different way.

I tried the suggestions here and after redetecting the HDD (with LBA enabled), deleting the partition info, repartitioning, and reformatting, I was able to install Windows XP successfully. Got through the installer without a hitch and finally got into the Windows desktop.

So, all set, I got myself into installing Ubuntu then.

Booted from the Feisty install CD and started the install process. From the partitioner menu selected the guided option to take the maximum usable space. In the installaton summary, Windows XP Pro was listed, so I set everything in auto pilot.

When I rebooted the computer, Ubuntu was working perfectly. So I restarted and went back to check how XP was doing. After I selected to boot to XP from Grub, i got the splash screen, and a few moments afterward, a BSOD with the next message.

------------------
A problem as been detected and windows has been shut down to prevent damage to your computer.
Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check you hard drive to make sure it is properly configure and terrminated Run ChKDSK /F to check for Hard drive corruption, and restart your computer. 

Technical Information:
STOP 0x0000007b ...

-------------------
Poof. Windows died. No getting into it, neither in safe mode nor in command line safe mode.
I tried booting from the XP installer CD and going into the recovery console. The thing wouldn't display dir info for drive C:, just an error message. When I tried

chkdsk /r

I only got an error message that said there are 1 or more problems that couldn't be solved.

So I got now a functional Ubuntu, but a broken Windows, even though it was working fine before. 

What can I do next?

---

### Post by logos34 on 2007-08-17
> **benkyoto said:**
> What can I do next?

Run a S.M.A.R.T diagnostic--maybe the windows part of the hard disk is damaged in some way.

> sudo apt-get install smartmontools

sudo smartctl -a /dev/sda

Did you reformat using NTFS?  Whatever filesystem you used, you should have done a full format (not a quick format) before XP install. 

It appears you've checked all the BIOS settings and hardware config for errors.     

Since you're pre-partitioning everything beforehand and not shrinking windows to make room for linux it can't be anything related to that.

The problem is clearly on the windows side--grub chainloads windows which then fails.  But it's obviously linux-related because windows works until you install ubuntu on partitions 2-4.  

Are you using just the programs on the XP and Ubuntu install CDs to repartition and reformat?

---

### Post by benkyoto on 2007-08-19
I was able to solve the problem. What I did is the following.

1. Confirmed that all BIOS settings were OK (HDD and other peripherals recognized, LBA on, no RAID,etc)
2. Booted from XP install disk. Erased the partition table and repartitioned. Formatted (not quick)  the partition to NTFS. Since I was using an XP original (not SP2) install disk, the partitioning tool didn't recognize the full 250 GB of the drive right away, only the first 130Gb or so, so I let it go that way.
3. Confirmed the successful installation of Win XP
4. Booted the PC from the Ubuntu Feisty Fawn install CD.
5. Fired up the installer and selected all the options as usual, but this time I went for manual partitioning of the remaining disk space (not guided). I ordered the partitions this way (if I remember well)
    1----Win NTFS ~130Gb primary boot
    2----boot / ext3 4096 Mb logical
    3----swap 2048 Mb logical
    4----linux ext3 ~110Gb logical
I was reading a lot around and this *could* be related to some weird first-1024-cylinder limit for the boot-related partitions. To put it into plain English, it seems to be better to put the bootable partitions in the front, which the guided installation did not.
6. Confirmed that Ubuntu was properly installed. Rebooted.
7. Selected Windows XP in the Grub menu. If worked perfectly too.

So what I learned here. If the disk you're using is not brand new:
1. It is necessary to redetect it in the BIOS and manually select LBA mode before doing anything else (some BIOS don't detect that setting). If you happen to change the LBA mode later on or unplug the same HDD and redetect it (so the BIOS doesn't recognize the LBA mode), it becomes unreadable.
2. One has to ERASE the partition table, REPARTITION and perfom a FULL format of the HDD. Whenever I failed to do any of these tree with the intention of saving time, the Windows bootup seq went awry and I ended up wasting a lot more time.
3. Better don't go with the guided partition process that the Ubuntu installer offers. It's wonderful when one installs only Ubuntu (I have another multiboot, double HDD desktop that purrs beautifully), but it doesn't seem to handle all the Windows quirks well when installing in a shared HDD. If you know what you want, manual is the way to go.
4. Be patient. You know it's all Windows fault, but you cannot live without it (just for the moment) :roll:

Thanks a lot  for your help and advice, logos. It was very helpful.

BTW now I have a different problem (xserv crashed when I installed a new PCI card -PCI to PCMCIA bridge-). Plus I don't know if I can get the TV capture card that I have (a PCMCIA card from my old previous laptop) to work under Ubuntu. If I was able to do that, I could pretty much ditch XP. But since these two issues are completely unrelated, I'll do my research first an post a different thread if necessary. Cheers.

---

### Post by logos34 on 2007-08-20
I'm happy to see you finally got this dual boot setup working!  Your persistence paid off.

I could be wrong but I think using NTFS and doing a FULL format was the key here (and apparently the BIOS drive detect settings).  But the 1024 cylinder (~8 GB) limit is an old issue--even without the service packs windows XP has 28-bit LBA support (i..e. address up to 137 GB disk space)...SP1 adds 48-bit support.
> 
1----Win NTFS ~130Gb primary boot
**2----boot / ext3 4096 Mb logical**
3----swap 2048 Mb logical
**4----linux ext3 ~110Gb logical**

Is #2 your root (/) partition and #4 a separate /home partition?  I assume that's it, because if 2 is a /boot partition and 4 is root, then you're wasting a lot of space (/boot should only be at most 50-100 **MB**)

---

