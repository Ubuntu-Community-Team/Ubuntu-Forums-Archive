---
title: "New Hardy install GRUB issue"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by sluthy on 2008-05-03
Hello all, first time poster, first time user.

I have just installed Hardy Server amd64 on my new PC (no other data, fresh HDDs). All HDDs are SATA.

Pentium E2140
Gigabyte GA-G33M-DS2R
4 x 320GB Seagate HDDS in motherboard RAID5 (and/or software RAID, will get to that)
1 x 80GB Samsung HDD

I want to install the OS on the 80GB and leave the RAID to data. The installer sees the 80GB as sdc, the four RAID HDDs as sda, sdb, sdd and sde (when I plug in a USB stick, it comes up as sdf).

First time, I install onto sdc with standard guided partitioning and leave the RAID as is (empty). Installs fine, 'please reboot'. I do so, and I get:

Loading GRUB stage1.5.
(...)
Error 21. :(

From what I've read, this means the menu.lst may be stuffed, or something else. According to [this]("http://ubuntuforums.org/showpost.php?p=4712026&postcount=22") post, it may be a corrupted GRUB install due to an apt-get conflict in Hardy. So accordingly, I reinstall while removing the network cable during the partitioning stage. I also add a 100MB /boot partition at the beginning of the drive as the automatic partitioner didn't create one (?). I then automatic-ed the remaining space and continued as per last time.

Reboot - same error. :mad: Grr.

I booted up with SystemRescueCD (what a PITA that is) and copied the menu.lst file (from /boot/grub/) onto my USB stick in case anyone here needs to analyse it. Does anybody know where to go from here? I've heard a lot of talk about Super GRUB Disk, but I was kind of hoping I could get away without burning another disc (I've spent about 15 CD-Rs on this bloody server already, long story). I will if I have to though.

When I do get this up and running I would like to be able to set u some network printers, but I realise this question is a bit long winded and involved, so I'll ask that question in another thread. Thanks in advance for any help. :)

---

### Post by Pumalite on 2008-05-04
Have you read this?:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
Evry time you install Grub; it will try to do it to your Raid.

---

### Post by sluthy on 2008-05-04
So if I'm solely running Ubuntu on this server, there's no need for a fakeRAID since it's no more effective than a softRAID? If I delete the fakeRAID and go through the initial installer as if the other drives are not used (and set up the RAID post-install), should it work?

Or can I just edit the existing GRUB to point to the right location? Or is that stuffed?

---

### Post by Pumalite on 2008-05-04
I'm no Raid expert, but I have the feeling that you cannot reconstitute your Raid after the installation. Better install in separate drive and install Grub to it's own partition. Later you boot it with Super Grub or changing the order of boot in BIOS.

---

### Post by sluthy on 2008-05-04
...which is what I've done hopefully (80GB drive has /boot, / and swap, rest unused). So if I use Super GRUB to edit the existing GRUB, could that work?

---

### Post by Pumalite on 2008-05-04
No. You boot Super Grub and it will boot Ubuntu.

---

### Post by hiec on 2008-05-04
I was a linux first time user when I set up my system (OS for this setup was 7.04 back then). I use two SATA drives in Linux software RAID and a PATA drive for backups. It took me a long time to get things working. Grub is, as far as I know, not aware of RAID. My solution was to use the alternative CD for the installation. The text-based installer has an option that allows you to configure software RAID during the installation process.

Useful to find out what's going on is to learn the grub annotation for HDDs.

IIRC, it works like that:

Linux annotation ---> Grub annotation

/dev/sda ---> (hdd0)
/dev/sda3 ---> (hdd0,2)

I think(!) /dev/sda is not necessarily (hdd0)! It could be (hdd1) or (hhd2) and so on.

---

### Post by sluthy on 2008-05-04
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=574bdbd7-b503-4f79-b221-902a8191a942 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-server
root		(hd2,0)
kernel		/vmlinuz-2.6.24-16-server root=UUID=574bdbd7-b503-4f79-b221-902a8191a942 ro quiet splash
initrd		/initrd.img-2.6.24-16-server
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-server (recovery mode)
root		(hd2,0)
kernel		/vmlinuz-2.6.24-16-server root=UUID=574bdbd7-b503-4f79-b221-902a8191a942 ro single
initrd		/initrd.img-2.6.24-16-server

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


From what I can see, it's pointing to the correct partition, assuming sda=hd0, sdb=hd1 and sdc=hd2 (making /boot hd2,0).

I did notice however, I didn't see a grub.conf file. Everything else seemed there but no conf file like my old Fedora install. Should there be one?

---

### Post by Pumalite on 2008-05-04
No conf. file in Hardy.

---

### Post by sluthy on 2008-05-04
Well, it's working now - sort of.

I deleted the fakeRAID and softRAID - for now, the four RAID HDDs are unused. I then set up:

#1 100MB /boot ext3
#3 remainder / ext3
#2 4GB swap

on the 80GB. Continued on as per normal, and it boots perfectly. Huzzah :)

First thing on my agenda is getting printing working (we've been without a printer for months because of this), then I'll sort out how to bring the RAID back. Soon hopefully - the 200GB drive on this PC is starting to show signs of wear and I'll lose everything.

---

### Post by Pumalite on 2008-05-04
Fake Raid and Software Raids are a waste of time. Unless you have the real thing; hardware Raids, it's not worth your effort. You can use your other drives for a separate /home for Ubuntu and for storage

---

### Post by sluthy on 2008-05-04
I was going to use it as a RAID5 general storage area for shared music/movies/files etc for the whole family, with the RAID5 as backup (I know it's not the best backup solution but until BD-Rs are available in cheap spindles I am NOT backing up that much to discs, and I can't afford a tape drive).

---

### Post by sluthy on 2008-05-07
Bump - does anybody know how to set up a RAID post-install?

---

### Post by LordVeovis on 2008-05-09
I know a little bit... only because I have been trying for a week myself to get my raid to work... 

[http://ubuntuforums.org/search.php?searchid=40914715](http://ubuntuforums.org/search.php?searchid=40914715)

If you install mdadm u can use that to manage raid configurations.
I don't know much about using mdadm, but it is what does the software raids.

If you wanted to try your luck again with a fakeraid, install dmraid.  gparted should recognize the fakeraid with dmraid, and will also recognize a software raid after it has been created with mdadm.  There are walkthrus about making a software raid with mdadm floating about...

---

