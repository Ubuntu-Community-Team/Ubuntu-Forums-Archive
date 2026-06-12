---
title: "UbuntuDesktop rts intel, bypass intell RTS/internal hard drives, install external usb"
date: 2024-04-24
forum: Installation &amp; Upgrades
---

### Post by rico0012 on 2024-04-24
Greetings;
Upon using the install setup I got the message to change intel RTS settings for internal hard drives.  I just want to not boot from the internal drives and boot from external drives.  Any suggestions?  UEFI, 64-bit x86_64  Thanks.

---

### Post by oldfred on 2024-04-24
What version of Ubuntu?
Older version of Ubuntu and flavors use Ubiquity installer with this bug for any install to second or external drive.
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Some disconnect internal drive, some are able to temporarily turn off drive in UEFI settings.
New versions of Ubuntu use Subiquity installer, Lubuntu & now Kubuntu 24.04  use Calamares installer. Both will allow direct install of grub boot loader to an ESP on external drive if UEFI system.

If older system, you may want lighter weight flavor as Ubuntu is for newer systems. 
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)
I happen to like Kubuntu which is more of a mid-weight flavor but I have had it work on old system as well as my newer system.

I prefer to gpt partition in advance with gparted so I can be sure to have an ESP - efi system partition on external drive.
Note if drive is very old MBR(msdos) conversion to gpt will totally erase it.
You can also use gparted but must change device label to gpt for default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting to add partitions.

You may want to wait a day or two as 24.04 is about to be released.

---

### Post by rico0012 on 2024-04-24
I tried Ubuntu Mate: linuxmint-21.3-mate-64bit.iso
will probably wait 2 days hopefully the newer ubuntu will provide a solution.  I just expected ubuntu to erase the external drive or USB drive and am not aware of any uefi formatting needed.  it's a UEFI only pc.  Thanks for the solutions.
> **oldfred said:**
> What version of Ubuntu?
Older version of Ubuntu and flavors use Ubiquity installer with this bug for any install to second or external drive.
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Some disconnect internal drive, some are able to temporarily turn off drive in UEFI settings.
New versions of Ubuntu use Subiquity installer, Lubuntu & now Kubuntu 24.04  use Calamares installer. Both will allow direct install of grub boot loader to an ESP on external drive if UEFI system.

If older system, you may want lighter weight flavor as Ubuntu is for newer systems. 
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)
I happen to like Kubuntu which is more of a mid-weight flavor but I have had it work on old system as well as my newer system.

I prefer to gpt partition in advance with gparted so I can be sure to have an ESP - efi system partition on external drive.
Note if drive is very old MBR(msdos) conversion to gpt will totally erase it.
You can also use gparted but must change device label to gpt for default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting to add partitions.

You may want to wait a day or two as 24.04 is about to be released.

---

### Post by oldfred on 2024-04-24
My Dell which is UEFI only, installed with RAID on using VMD driver which previously I did not know about. 
I installed Kubuntu 22.04, but will be installing 24.04 soon. I have several test installs of Kubuntu 24.04 but will totally reinstall it once finalized so all development settings and updates are removed.

---

### Post by rico0012 on 2024-04-25
I don't know how what your saying can help me as I sucessfully installed it!  :-) But I can give you information.  I used other software besides rufus such as belana etcher because rufus asked me between.  dd and iso mode when flashing the media and seemed to install grub to the install usb.  I reflashed using belana etcher.
Keeping Windows 11 - installing allongside
I removed the intel device driver from windows for rst premium.  You probably won't need to ill explain in the next steps.
1.  Tried AHCI and it wouldn't boot (before installing ubuntu).
2.  Selected instead the hide RAID option *RAID disabled* (forget what it's called but will try to post screenshot Edit - Cant upload: options listed in SATA Operation: Disabled, AHCI, RAID On) I think its under System Configuration

3.  Booted the ubuntu install usb and selected graphics help mode.  Using tv not monitor.
      A.  Created an Ext4 partition on a blank usb drive.  
  DOCUMENTATION OF DRIVES AND DRIVE PATHS    
You may want to create a meaningful label for it. and document the drive paths.

4. Tried to select custom drives I wanted but partitions are confusing/ so didn't just did alongside.
MAKE DRIVE IMAGE/BACKUPS

It was after install I realized I probably should have made a backup drive image.  Important data was on other drives...
You many want to create external windows boot media/ Image the drive in case run into problems....

5.  After install (creating standard, not privilaged username and password) I restarted.
6.  Ubuntu boots before windows in the EUFI boot sequence...  
7.  you can change settings for the computers F12 boot menu, by going in the so called: bios settings.

---

### Post by rico0012 on 2024-04-25
**_Project/ Task Failed _** This info on RST not help others solve my problem of installing to an external drive. but may give ideas to them. 

 I would have to know how to :
1.  Use the wizard during install to set up custom partitions.  2.  Know how to make drive bootable.  3.  know how windows boot menu worked ...Because I did not feel comfortable with creating boot menu either for Linux or Windows I didn't...  Windows 10 11 can now add bootable iso/images to its bootloder.  

To oldfred: in the past there was a wubi installer it may have been easier.  Couldn't find a github binary, up to date.  A problem was I wasn't familiar with gparted (same from past installs) and  couldn't understand my logical vs physical organization of drives and partitions.

---

### Post by oldfred on 2024-04-25
Wubi is long obsolete.
For users that are primarily Windows users, there is WSL  a limited Ubuntu install inside Windows.
[https://learn.microsoft.com/en-us/windows/wsl/install](https://learn.microsoft.com/en-us/windows/wsl/install)
A full virtual install would be better for many, or dual boot.

Different vendors & different models often have UEFI and configuration differences.

You can see all you partitions with this from command line in Ubuntu.
lsblk -f
With gpt there are not any logical partiitons as they all all primary. It was old MBR(msdos) that had primary, and logical partitions inside  an extended partition.

---

