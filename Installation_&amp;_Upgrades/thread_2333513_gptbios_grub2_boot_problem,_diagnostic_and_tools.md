---
title: "gpt/bios grub2 boot problem, diagnostic and tools"
date: 2016-08-10
forum: Installation &amp; Upgrades
---

### Post by einhexenmeister on 2016-08-10
sorry for the lengthy question


i have a 200 gb ssd formated as gpt with protective bios and grub2 (kubuntu 1404 did this back in 2014)

amd 8 core mobo with uefi bios

a year ago
after a clonzilla from this ssd to a second ssd (same type) with cloning or copying boot and mbr by clonezilla resulted in will not boot

can't boot, but a friend helped me to fix a grub2 issue ... don't remember what he did, but it worked fine afterwards

now
did clonezilla again with same result ... no longer booting ... friend not avail, so i worked on it

i booted from rescatux / super-grub usb stick and did the following tests

gparted

sda1 500 mb ext2 (my /boot)
sda4 2 mb unknown
sda2 200 gb ext2 (my /root and home and usr/local)
sda3 11 gb unknown

initially i ran boot-info and it complained that on sda1 and sda2 the core.img file can't be found at xxxxxxx

boot from kubuntu live 1604 (not 1404)
i did a mount of sda2 /mnt and sda1 /mnt/boot and a bunch more mount --bind xxx as instructed
did a chroot
sudo grub-install /dev/sda and it succeeded
note : my kubuntu is 64 bit, but the grub-install did a i-386 flavour ???
ctrl-D to exit chroot
umount all prev mounts
and reboot

no success

boot from rescatux stick again

now boot-info shows no longer "can't find core.img at xxxxx" for partition sda1 /boot
sda2 /root still shows can't find core.img

zeroed 1st 512 bytes of sda2 assume mbr space with dd

now boot-info no longer looking for image on sda2 /root

tried either boot, esp or bios-rub flags on sda1 /boot and or 2nd unknown 2mb partition after sda1, but doesn't boot

boot from rescatux stick again

ran fsck on sda1 /boot and sda2 /root with result "clean"

used wxhexeditor to look at

ssd (globally) and it shows mbr image on 1st 512 bytes

ssd.part1 assuming sda1 /boot and shows data (possibly core.img) which contains "loading" and "Geom Read  Error" as readable pieces within 1st 500 bytes

ssd.part2 assuming 2mb unknown partition containing 0s ... scary if this is supposed to be the core.img perhaps

ssd.part3  assuming sda2 /root all 0s was cleared with dd 512 bytes

ssd.part4 assuming 11 gb unknown format at end of ssd containing surprisingly same signature as ssd.part1 /boot ??? core.img

also boot-info showed
Boot sector type:  Grub2's core.img on this unknow filesystem partition at the end of the ssd ... don't know how it got there ... maybe during the 1st grub repair a year ago by friend


i'll include at the end part of the boot-info

boot attempt symptoms :

bios splash -> f2 -> f8 to get boot menu and selecting ssd
upon enter pc seems to power down and fan spins down ... a few secs later boots up again and again and again


if i boot from rescatux or kubuntu life i can mount both partitions and have access to all files as it seems all well as a "clean" result from the unmounted partitions with fsck

i do not know of anything else to get more diagnostic info

i also don't know on how to check the gpt partition info and or mbr content for validity and proper linkage

there are also a few question

1) is it legal that the grub-install installs a i-386 grub2 in a 64 bit kubuntu os

1a) is there an issue with restoring grub2 from a 1604 disk on a 1404 install


2) the ssd shows the following partitions

sda seems to show a valid mbr as shown in wxhexeditor ... don't know another tool to look at sector content

sda1 500 mb ext2 (/boot) ... seems to have possibly core.img at 1st 512 bytes 

sda4 2 mb unknown (following sda1, is this supposed to hold the core.img) ... shows 0s ... i didn't touch it

sda2 200 gb ext2 (/root and all else) ... 1st 512 bytes 0s as cleared my dd 

sda3 11 gb unknown (remainder of ssd) seems to also containing core.img, maybe from the 1st grub boot fix a year ago


3) i assume that the mbr on sda 1st 512 bytes contains a valid mbr by looking at it ... don't know of tools to verify validity and linkage

i do not know on how to verify or get info on the linkage of the mbr for continuation

4) sda1 (1st partition) contains what looks like core.img in the 1st 512 bytes ... the reminder "clears" fsck

5) if sda4 2 mb unknown (2nd partition ... is 0s) is this supposed to hold core.img

6) sda2 200 gb ext2 (3rd partition with 1st 512 bytes 0 seems ok since fsck indicates "clear")

7) if the mbr at the 1st 512 bytes of the ssd is correct, where does it link to and how to verify or change it

8) is it correct that the 1st partition ext2 (boot) contains what seems to be core.img in the 1st 512 bytes

9) is the core.img supposed to be contained in the following 2mb partition currently holding 0s any tools to put the core.img onto it since it's 0s

10) is it correct that the 3rd partition ext2 with holding /root and all else has the 1st 512 bytes being 0s

it's very hard to find answers to any of the above loq level questions about the disk architecture, it's link addresses and tools to verivy and correct or change the settings


any help is highly appreciated, cheers EinHexenMeister



gdisk printout

GPT fdisk (gdisk) version 0.8.10

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 468862128 sectors, 223.6 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 02FA083F-9F81-4010-9DAC-B92B681C64E6
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 468862094
Partitions will be aligned on 2048-sector boundaries
Total free space is 3181 sectors (1.6 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1001471   488.0 MiB   EF00 
   2         1005568       444370943   211.4 GiB   8300 
   3       444370944       468860927   11.7 GiB    8200 
   4         1001472         1005567   2.0 MiB     8300 


boot-info part

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 2048
    of the same hard drive for core.img. core.img is at this location.
 => libparted MBR boot code is installed in the MBR of /dev/sdb.
 => libparted MBR boot code is installed in the MBR of /dev/sdc.
 => No known boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub2's core.img
    Boot sector info:
    Operating System: 
    Boot files:        /grub/grub.cfg /grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 14.04.5 LTS
    Boot files:        /etc/fstab

sda3: __________________________________________________________________________

    File system:      
    Boot sector type:  -
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:      
    Boot sector type:  Grub2's core.img
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

---

### Post by einhexenmeister on 2016-08-11
finally found the solution

conclusion :

i have a gpt/bios setup on sda as can be seen with the parted printout

Model: ATA INTEL SSDSC2BW24 (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End    Size    File system  Name  Flags
1      1049kB  513MB  512MB   ext2
4      513MB   515MB  2097kB               bios_grub
2      515MB   228GB  227GB   ext2
3      228GB   240GB  12.5GB

number 1 sda1 ext2 /boot
number 2 sda2 ext2 /root and all others
number 4 sda4 not formatted 2 mb needs the bios_grub flag set and no other flabs, like boot, esp set on any other partitions

i did initially not have this flag set, which needs to be set before a grub-install procedure

after  i set this bios_grub flag on this unformatted 2 mb partition i did the  grub-install with mounts and chroot according to the link below and everything worked (booted normally as it did before

[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd-pendrive.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd-pendrive.html)

---

### Post by LostFarmer on 2016-08-11
>  is it legal that the grub-install installs a i-386 grub2 in a 64 bit kubuntu os
  Yes, one can install linux in csm/bios/mbr mode on a GPT disk ( not all comps will permit mbr booting on a GPT drive, mine will not).  That is when a bios_grub flagged partition is needed.

I do use and like program 'wxhexeditor' but if one is not careful , a lot of damage can be done to needed information for system to work.

---

