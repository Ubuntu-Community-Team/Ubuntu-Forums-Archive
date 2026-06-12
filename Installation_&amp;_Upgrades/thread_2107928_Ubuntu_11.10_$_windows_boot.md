---
title: "Ubuntu 11.10 $ windows boot"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by fredcarru on 2013-01-23
I have the following hardware
Motherboard    Asus with American megatrends BIOS giving F11 as a choice to boot from

1) CD/DVD
2) Samsung 1TB SATA 1 Ubuntu sda, Windows C:\
3) Samsung 500GB SATA 2 Ubuntu sdb, Windows unregognised
4) memorystick

    In October 2011 I installed windows XP Pro on sda with sdb disconected and Ubuntu 11.10 on sdb with sda disconnected. This resulted in an automatic boot to Windows, fine for other users.  If I wanted to boot Ubuntu I pressed F11 during BIOS and selected option 3.
    
On 22nd Feb 2013 I installed  "81 updates" to Ubuntu and the result was it automatically booted to Ubuntu and no mater which of the other boot options I choose it booted Ubuntu.
    
I did not expect this from Ubuntu. 

I recovered the original situation by booting with sdb disconnected and booting to XP recovery CD then choose recovery. Then
C:\WINDOWS\fixboot
C:\WINDOWS\fixmbr

    How can I avoid this in future upgrades?

---

### Post by dino99 on 2013-01-23
every new plugged hardware get a new uuid (which is not known by grub indeed, till you update it.)

So in your case, i suppose that using label instead of uuid is the best choice. But plgging/unplugging hardware is not a solution by the way, you might draw an other solution for your needs.

---

### Post by oldfred on 2013-01-23
Grub remembers the drive it installed into and should have reinstalled to that drive.

       #To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

    
       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by fredcarru on 2013-01-24
dino99     thanks for the comment.
oldfred    I think what you are saying is that because I installed Ubuntu with the windows drive disconnected grub knew nothing of it. Therefore when I ran the upgrades grub created a boot on sda which only booted to sdb. The recommendations you make would create a boot on drive sda which would give a choice of which os to load?

Unfortunately when I first installed Ubuntu 11.04 with both drives connected it screwed up the windows drive to the point where I had to use Gparted to format an NTFS partion and then I used the procedure of disconnecting as described above.

I guess I'll just have to resort to disconnecting sda whenever I upgrade Ubuntu, as I'm not willing to take that risk again. Other machines I've just installed Ubuntu work fine.

Thanks for the help I'll mark this solved

---

### Post by oldfred on 2013-01-24
Actually I do not understand how it updated incorrectly. New versions all save the drive full name not the device. So it should have updated to the correct drive. 

Unless somewhere you did install either windows boot loader to the Ubuntu drive or grub to the Windows drive.

---

### Post by fredcarru on 2013-01-24
oldfred
I believe that because I installed Ubuntu with sda disconnected so grub set up using sdb then when I ran the updates one of them updated grub and installed it causing it to copy the file from sdb to sda, which new nothing of Windows.
Hence my problem

when I run
sudo grub-probe -t device /boot/grub
It returns
/dev/sdb1

but I have reinstalled Windows boot and mbr. If it happens again I'll try grub-probe before doing anything else and see if it returns sda1 and sdb1.

Out of interest the $ dollar symbol in the title should have been & ampersand. I'm using a UK keyboard but it appeared OK until I submitted the reply.

---

### Post by oldfred on 2013-01-24
That says it is reinstalling to a partition sdb1, not even the MBR sdb??

What does this show?
sudo debconf-show grub-pc

---

### Post by grahammechanical on 2013-01-24
Am I correct in thinking that you have two version of Ubuntu installed? One version in sda and another version in sdb? 

Which version did you update? From time to time we get an update to Grub or to the kernel that will update the Grub configuration files and sometimes re-install Grub to the MBR. That should be fine if you are booting into the hard drive where the newly updated Grub configuration files are stored. But if you are booting into the other drive without inaccurate Grub configuration file that could explain why you can only boot Ubuntu.

Do you have more than one version of Ubuntu?

Regards.

---

### Post by fredcarru on 2013-01-25
oldfred
the result of
sudo debconf-show grub-pc 	
is
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-SAMSUNG_HD103SI_S1VSJ9JB606281
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: false
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 10

grahammechanical
if you refer to my original query I have Windows XP Pro on sda (C:\) and Ubuntu 11.10 on sdb, these were each installed with the other drive disconnected.

I do indeed have more than one Ubuntu. Ubuntu 11.10 on my desktop and 12.04 on my netbook. I also have Raspian (Debian) on my Raspberry Pi.

---

### Post by oldfred on 2013-01-25
Is this your Ubuntu drive?

> grub-pc/install_devices: /dev/disk/by-id/ata-SAMSUNG_HD103SI_S1VSJ9JB606281

---

