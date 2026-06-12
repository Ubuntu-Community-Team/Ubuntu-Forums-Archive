---
title: "Grub2 + RAID + Encryption + LVM driving me up the wall"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by gdaddy on 2010-03-03
Hi,

I've been trying for days and I just can't get this to work.

I pretty much follow this guide verbatim [http://www.howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system-p5](http://www.howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system-p5) - in fact I am so practised at it I can do it in about 5 minutes.

I have also tried following the guide but installing both hard drives.

I have tried removing grub2 and using grub (and just about every permutation of grub).

I have tried removing all the UUID references in crypttab, fstab and also changed the /etc/defaults/grub to not use UUID.

It just won't work.

So what happens.

On install boots fine, but if I remove either drive it either stops with Grub loading screen on Grub2 or it stops after Stage1.5 of grub.  When it finally drops I get an error saying Check cryptopts=source= bootarg cat /proc/cmdline or missing modules, devices, then later /dev/disk/by-uuid/<xxxx> does not exist

Any ideas?

Have run Boot Info Script when using both drives below
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/grub.

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

md2: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'

md1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'
mount: unknown filesystem type ''

md3: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'
mount: unknown filesystem type ''
mount: unknown filesystem type 'crypto_LUKS'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 15.3 GB, 15289286656 bytes
255 heads, 63 sectors/track, 1858 cylinders, total 29861888 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00099c65

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       498,014       497,952  fd Linux raid autodetect
/dev/sda2             498,015     2,457,944     1,959,930  fd Linux raid autodetect
/dev/sda3           2,457,945    12,225,464     9,767,520  fd Linux raid autodetect
/dev/sda4          12,225,465    14,185,394     1,959,930   5 Extended
/dev/sda5          12,225,528    14,185,394     1,959,867  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 15.9 GB, 15942549504 bytes
255 heads, 63 sectors/track, 1938 cylinders, total 31137792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d4719

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       498,014       497,952  fd Linux raid autodetect
/dev/sdb2             498,015     2,457,944     1,959,930  fd Linux raid autodetect
/dev/sdb3           2,457,945    12,225,464     9,767,520  fd Linux raid autodetect
/dev/sdb4          12,225,465    14,570,954     2,345,490   5 Extended
/dev/sdb5          12,225,528    14,570,954     2,345,427  fd Linux raid autodetect


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/md1_crypt f8a059ed-c929-4eea-8b2f-ad1f46e841ab   swap                                     
/dev/mapper/md2_crypt eb80e51e-ebc7-42f0-9bfd-97d8274b3369   ext4                                     
/dev/md0         fe7150b0-f9a3-4f90-aff4-f41f90457fd9   ext4                                     
/dev/md2         4a447fc6-3900-499e-a7de-3d33b624b888   crypto_LUKS                               
/dev/md3         55392b58-06d0-46de-ae61-72b9882c8bb4   crypto_LUKS                               
/dev/sda1        b0162122-3deb-3d3d-0e32-c0984ef61a94   linux_raid_member                               
/dev/sda2        948f36c6-beb3-fece-7ca4-22883c4a6551   linux_raid_member                               
/dev/sda3        2be7c484-44a3-0f30-cbed-27033da55193   linux_raid_member                               
/dev/sda5        a4cce4c5-96bd-801b-ab66-1a94328e4720   linux_raid_member                               
/dev/sdb1        b0162122-3deb-3d3d-0e32-c0984ef61a94   linux_raid_member                               
/dev/sdb2        948f36c6-beb3-fece-7ca4-22883c4a6551   linux_raid_member                               
/dev/sdb3        2be7c484-44a3-0f30-cbed-27033da55193   linux_raid_member                               
/dev/sdb5        a4cce4c5-96bd-801b-ab66-1a94328e4720   linux_raid_member                               

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
md1_crypt
md2_crypt

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/md2_crypt /                        ext4       (rw,errors=remount-ro)
/dev/md0         /boot                    ext4       (rw)


============================== md0/grub/grub.cfg: ==============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod raid
	insmod mdraid
	insmod ext2
	set root=(md0)
#	search --no-floppy --fs-uuid --set fe7150b0-f9a3-4f90-aff4-f41f90457fd9
	linux	/vmlinuz-2.6.31-14-generic root=/dev/mapper/md2_crypt ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod raid
	insmod mdraid
	insmod ext2
	set root=(md0)
	search --no-floppy --fs-uuid --set fe7150b0-f9a3-4f90-aff4-f41f90457fd9
	linux	/vmlinuz-2.6.31-14-generic root=/dev/mapper/md2_crypt ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

==================== md0: Location of files loaded by Grub: ====================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.31-14-generic
    .0GB: vmlinuz-2.6.31-14-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2
<removed>

Unknown BootLoader  on sda3
<removed>

Unknown BootLoader  on sda5
<removed>

Unknown BootLoader  on sdb2
<removed>

Unknown BootLoader  on sdb3
<removed>
Unknown BootLoader  on sdb5
<removed>
Unknown BootLoader  on md2
<removed>
Unknown BootLoader  on md1
<removed>
Unknown BootLoader  on md3
<removed>

```

---

### Post by gdaddy on 2010-03-03
When I remove sda and boot with LiveCD and run script - sdb is now named sda, and shows that it is searching for md0, although there is no RAID setup as LiveCD doesn't have mdadm as standard

---

### Post by Paloki on 2010-03-23
I used the same setup, little difference in partitions, but basically raid 1 using 2 disks, boot is standard, rest is lvm on encrypted raid 1 partition. This was done from the install cd.  Everything works fine, prompts me for password and finishes boot when both drives or connected. If I remove either drive then see grub statement flash by and then just a blinking cursor. I hook both drives up and and everything works fine. If need my configuration info as well let me know.

---

### Post by Nooki on 2010-04-23
I have the same problems. I installed the new Ubuntu 10.04 on two fresh 1TB drives, using the alternate CD. I decided to go full encrypted RAID1 drives (except /boot, which is RAID1 unencrypted).

Just for the story, using the alternate CD you have to follow this configuration order to do it:
1) Partition both drive equally
2) Configure RAID setup
3) Configure encryption
4) Use LVM to create logical volumes on top of encrypted RAID.

It's working flawlessy when both drives are connected. If I try to do a failure test, eg. unplugging one of the two drive, two things can happen:

[LIST=1]
[*]If I unplug SATA1 connected drive (bios labels it as "Master"), bios refuse to boot. It says that it cannot boot from the Slave drive or something along those lines. Would it be because there is no grub written in the MBR of my second drive?
[*]If I unplug the SATA2 connected drive (bios labels it as "Slave"), it boots, then stall on the same error message that the OP experienced  (Check cryptopts=source= bootarg...)
[/LIST]
Any news / developments regarding this issue would be highly appreciated.

---

### Post by brc816 on 2010-04-26
I'm looking into putting GRUB2 onto an LVM-based 1TB USB drive (without encryption), but I looked at the GRUB/GRUB2 bug
listing and there are a number of open bugs that appear to prevent me. (I have succeeded by using a separate ext4-formatted /boot
partition and carefully copying each OS' boot files into separate directories under /boot, e.g. /boot/ubuntu, which works,
but it is a management headache.)

I don't know which, if any, of the open bugs would apply to your specific configuration/problem, but take a look at:

[http://savannah.gnu.org/bugs/?group=grub]("http://savannah.gnu.org/bugs/?group=grub")

---

### Post by Nooki on 2010-04-26
Yeah. Way too many conflicting or deprecated bug reports. The best way is to try it! But I do remember having read somewhere that Grub2 was now able to boot from LVM partition (unencrypted!). If it's not working, you might reconsider the necessity to have /boot on LVM. I just chose to made it big enough so I wouldn't ever need to resize it later (500 MB) and chose a primary, unencrypted partition that I put in RAID1 configuration. Having a single primary partition does not stop you from having the rest of your drive partitioned using LVM. At least I think this is what I did with my setup.

---

### Post by brc816 on 2010-05-06
Well, I'm pleased to report some positive results, but not a complete success.

I was able to use 'parted' to create a 1MB partition at the start of the USB drive, then set its type to bios_grub. I then used the Alternate CD to create an LVM, and a few PVs within the LVM, including one for swap.

Once I did that, I was able to install LL (once I made bloody sure that the installation process actually created an ext4 fs in the desired PV!), and it boots and seems to work quite nicely, even with swap in a PV, and plays well with the GPT on that drive.

I am doing this on a single USB drive, so no RAID is involved, nor am I doing anything with encryption.

However, the one problem I am having is that GRUB2 does not work properly with multiple drives on the same "string" and gets very confused when trying to boot other stuff in my system. Briefly, I have a large laptop with two hard drives in it. Drive 0 has Windows XP factory installed, and Drive 1 has my day-to-day openSUSE 11.2 installation, and (old) GRUB (0.97) is installed in the MBR of drive 0 and boots either drive/system nicely.

However, the GRUB2 menu on the USB drive lists all the OS's in the system, but when I attempt to boot, say, Windows XP off of the first hard drive, it fails, complaining of 'no such device' and gives a UUID, and claims "invalid signature". Booting openSUSE 11.2 seems to start its boot process, but it fails just after trying to mount the root device, and dumps me to a shell.

Interestingly, the same thing happens with the simple installation I made to a 16GB Cruzer thumbdrive. In both cases, when I invoke the GRUB command line, and do an 'ls', the drives and partitions are listed in a different order from what 'grub.cfg' seems to expect. I had problems similar to this when I set up a USB drive under (old) GRUB (0.97) but was able to work around it by manually editing menu.lst (or grub.conf, depending on the distro). Obviously, that's not going to be the case with GRUB2. Further, when I have multiple USB drives installed, only the first 'spindle' on each string is displayed by 'ls' - I can no longer "see" my second hard drive which rather complicates (i.e., prevents) booting off of it. Trying to chainload back to an (old) GRUB (0.97) drive doesn't work, period.

---

### Post by tonywhelan on 2010-10-22
Did you ever get anywhere with this problem? I have had the same problem with Ubuntu 9 and 10. I can make raid work ok without encryption, but not with encryption set up. So I assume the encryption software is the issue.

I tried using CentOS to get encrypted raid 1 and that worked as required - will boot off either disk.  But CentOS won't play wth my onboard NIC so that's not an option. There seems to be no real explanation out there as to why Ubuntu does not work properly with encrypted raid.

---

### Post by tonywhelan on 2010-10-22
There are some active bugs about this:
[https://bugs.launchpad.net/ubuntu/+s...dm/+bug/488317](https://bugs.launchpad.net/ubuntu/+s...dm/+bug/488317)
[https://bugs.launchpad.net/ubuntu/+s...up/+bug/251164](https://bugs.launchpad.net/ubuntu/+s...up/+bug/251164)

But they don't seem to be getting much attention, so I won't hold my breath.

---

