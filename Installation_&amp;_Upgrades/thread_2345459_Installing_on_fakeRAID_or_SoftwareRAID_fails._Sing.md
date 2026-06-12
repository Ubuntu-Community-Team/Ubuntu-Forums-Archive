---
title: "Installing on fakeRAID or SoftwareRAID fails. Single SSD install stuck after login!"
date: 2016-12-04
forum: Installation &amp; Upgrades
---

### Post by notbad on 2016-12-04
Hi there,

so my story:

I've had 16.04 installed and fully working on a single SSD, but I needed more space so I bought another same SSD and wanted to do it in fakeRAID 0. In my UEFI BIOS I've created an RAID 0 array and started my new installation... Everytime I get GRUB failed to install. I've tried different locations for GRUB. Nothing helped. As far as I got was Blinking cursor on the top left corner.

Same was with SoftwareRAID. Sometimes the installation hangs at 'force UEFI install'. As far as  got was GRUB rescue...

And now the worst part: the installation fails on a single SSD now too!!!! As far as I get after installation is the gdm login screen, after entering pass login stucked at grey screen with cursor. no TTY's work. Just hard reset!

What I've had tried so far:

/etc/gdm3/custom.conf - disable WAYLAND - no luck!
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) - didnt work
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) - didnt work!
[https://gist.github.com/umpirsky/6ee1f870e759815333c8](https://gist.github.com/umpirsky/6ee1f870e759815333c8) - no luck
SIMPLE INSTALLATION DOES NOT WORK ANYMORE (16.04 and 16.10) - stuck at login screen!

XUBUNTU installation worked on one SSD!!! Did not try RAID.

What am I missing? What am I doing wrong?

The System is used as dual boot system with macOS.

System Spec:

Asus Sabertooth Z77 Motherboard
2x SanDisk Extreme PRO 480GB SSD's on Intel Chipset
1x Crucial BX200 480GB SSD for macOS on AsMedia Chipset

**What I want to do is a simple installation with RAID 0**

Any suggestions?

---

### Post by oldfred on 2016-12-04
Once you change to RAID, the drive has RAID meta-data which interferes with grub install.
You can remove the meta-data with dmraid.
       Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)

The desktop installer has not supported RAID.
Back with 12.04 there was an alternative installer non gui based or the server installer for RAID.
They discontinued the alternative installer and said to use server installer or just install 12.04 and upgrade. And they would add LVM and RAID to desktop eventually.
Desktop does now support LVM, and recognizes RAID, but they have not gotten the grub install correct yet.

Most RAID still installs grub to drive like sda or sdb.
But fakeRAID has to install grub to the root of the RAID or something like this:
       
 "fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0 
    
       
 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04.
15.04 or later now uses mdadm to support intel fakeraids  


 Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by notbad on 2016-12-05
After numerous failed attempts I'm giving up with raid.

Now what I'm trying to do is to merge those ssds into one with lvm. But the problem is that after installing and rebooting and entering password the system hangs with grey screen and cursor. Nothing is working. Just hard reset.

Before I had fully working Ubuntu gnome 16.04 installation. Even 16.04 doesn't install and work anymore...

Strange is that Ubuntu 16.10 installation is working. But I need gnome...

---

