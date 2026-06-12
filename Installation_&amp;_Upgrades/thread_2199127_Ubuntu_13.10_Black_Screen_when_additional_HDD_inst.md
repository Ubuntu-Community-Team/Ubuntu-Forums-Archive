---
title: "Ubuntu 13.10 Black Screen when additional HDD installed"
date: 2014-01-12
forum: Installation &amp; Upgrades
---

### Post by cwblewitt on 2014-01-12
My upgrade from 12.04 to 13.10 has been a painful journey.  After auto-update from 13.04 to 13.10 I was not able to reboot - getting a 'black screen'.  No live CDs would boot - I kept dropping into BusyBox with a initramfs prompt.

I finally was able to install 13.10 by installing from LAN, removing all HDDs except the system disk.  All working fine, and reboot no problem.

Now I've added an additional HDD I am getting a 'black screen with flashing prompt' immediately after BIOS. The additional HDD is not new, but has been reformatted (a single primary partition) using GParted as EXT4 with no flags showing.

If I remove the second HDD all boots okay. 

Ubuntu 13.10 32bit is a standard Desktop install + GParted + TeamViewer + Chrome + LastPass + Everpad.

I'm assuming my black screen is not video related (boots okay on one HDD).  Thought maybe the second HDD may have a MBR but GParted doesn't show a boot flag.  The newer HDD works fine on this system if I do a hot install (connect while Ubuntu is running), but will not allow reboot.


Packard Bell ixtreme M5741
i3 processor
Bought in 2010
No additional hardware.
BIOS Information: American Megatrends Inc. | Version: P01-B1 | Release Date: 03/23/2010.  BIOS set to DEFAULT.

---

### Post by tfrue on 2014-01-12
Try and live boot Ubuntu and use fdisk, gparted, or parted with both HDD to erase all the partitions on all your drives, then install to the appropriate HDD with the bootloader (grub) being installed to to the first HDD (/dev/sda). See how that works.

Chris

---

### Post by cwblewitt on 2014-01-12
Thanks for the response.  System will not boot with liveCD - System drops into initramfs prompt after GRUB.  Old partitions on the new disks have been deleted and re-formatted with single new EXT4 partition using GParted.

With the additional HDDs I get black screen with flashing curser immediately after BIOS - before purple screen or GRUB.

---

### Post by tfrue on 2014-01-12
Sorry, I just re read the intro sentence of the OP and noticed the won't boot CD's lol. Does your computer support UEFI boot? Can you disable secure boot and enable legecy boot? And I've never heard of a computer that is unable to boot a CD, so I'm guessing that you have secure boot enabled.

Chris

---

### Post by tfrue on 2014-01-12
If you do get live boot to work, try and install boot-repair so I can have a more detailed problem to help you.

Go to this site for installing and using boot-repair
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cwblewitt on 2014-01-12
I can boot from other CDs including Win7, Spinrite, DiskTools etc. but not a 13.10 CD (that will boot on other machines).  I do not have any Secure Boot options, and no mention of UEFI.  I think this 2010 PC predates UEFI??

I have run boot-repair using default.  This did not resolve the issue.  Results here [http://paste.ubuntu.com/6740049/](http://paste.ubuntu.com/6740049/).  It did say "The boot files of [The OS now in use - Ubuntu 13.10] are far from the  start of the disk. Your BIOS may not detect them. You may want to retry  after creating a /boot partition (EXT4, >200MB, start of the disk).  This can be performed via tools such as gParted. Then select this  partition via the [Separate /boot partition:] option of [Boot Repair]"

 - I cannot fix this without being able to boot from LiveCD!

---

### Post by tfrue on 2014-01-13
Try and change the boot order in BIOS, or do a One Time Boot from BIOS and choose the cd. I would try once with the Ubuntu disk, then maybe try a different Ubuntu version like 13.04 disk, then maybe Gparted or LinixRescueRemix. If that doesn't work, try a USB and see if that works.

Here is you /etc/fstab file from when you installed
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdf1 during installation
UUID=88dd0bee-c0af-4d1a-b22c-c678e02649ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdf5 during installation
#UUID=fdaeceec-6a70-4c9a-a35c-5f3a8d3c095d none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
This might be of interest too:> ========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf 
So grub might be trying to pull the files from the /dev/sdf1 partition when the second HDD rather than /dev/sda, so I would back up all my data, plug all my drives in, live boot Ubuntu 13.04 or whatever version you want, or Gparted if that doesn't work, format all the drives at once, and then re-install grub2 and Ubuntu on the new /dev/sda.

We could try and troubleshoot more but I would need you to download LinuxSecureRemix or other distro to use boot-repair, and install the .iso to a disk, then plug in all your drives, and do a One Time Boot from the CD or USB and post another boot-repair with all the drives.

Chris

---

### Post by cwblewitt on 2014-01-13
Thanks for the support so far.  I'm downloading the recommended ISOs now to perform boot repair, but will not have have chance to try anything more until tomorrow.

---

### Post by cwblewitt on 2014-01-15
tfrue,  thanks very much for your assistance.  The GParted live CD worked a treat.  I am still unable to boot an Ubuntu 13.10 CD, but have successfully re-installed it, with all disks inserted, using PXE boot.:popcorn:

---

### Post by tfrue on 2014-01-15
Glad to hear that, and no problem!

Have you tried to re-download the 13.10 ISO and burn that to the disk again? There may be a problem with the data on that disk, or something else, who knows? Since you're able to boot other CDs, I don't see why you're not able to use that one, so I'm assuming something went wrong.

Chris

---

### Post by cwblewitt on 2014-01-15
I tried two 13.10 ISOs, one 32 and one 64 bit, and had same results.  GParted worked no problem.  Both these ISOs work okay on my laptop!

---

### Post by tfrue on 2014-01-16
Hmm, that's crazy. Well, don't forget to mark this thread as solved, and have a great day!

Chris

---

