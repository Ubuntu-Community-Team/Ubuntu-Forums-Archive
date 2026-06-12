---
title: "New Ubuntu User: (initramfs) Prompt After Alternate CD Installation 9.10 w/ RAID"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by WhiteyWan on 2010-01-13
I am trying to install Ubuntu on a nvidia board which, based on the forums I have perused, is a FAKERaid chipset.  Originally I tried to install according to [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) to no avail.  I gave up and am resorting to breaking down my raid setup (thus losing my Windows XP installation) and using Linux's software raid (which seems to be the recommended method) with the Alternate CD install.  

I went in to the bios and completely disabled my board's RAID function. I then followed the instructions here: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) , except it popped up with a window advising me "one or more serial ATA RAID configurations have been found. Do you wish to activate these RAID devices?" which that page didn't mention.  I believe I selected "Yes".  Setting up the partitions I made (from beginning of disk to end of disk) a RAID1 200MB /boot partition, a RAID0 / partition (90GB?), free space not set up in RAID (approx 20GB for each SATA drive to later install Windows on [if that's even possible]) & then the SWAP partition 2GB at the end of one of the disks (is it OK that this one wasn't in RAID?).

The installation completed, as far as I can tell, without a hitch.  Except also of note:  my network card doesn't work in the installer (gives an error message about unable to configure dhcp) so i'm not connected to the internet.  Then I restart and the following appears:

[B]grub loading:
error: biosdisk read error.[/B]

Followed by what appears to be the Ubuntu loading splash (just a small white shape in the middle of the screen), and then: 

[B]gave up waiting for root device. *Common problems:*
- boot args (cat /proc/cmdline)
- check rootdelay= (did the system wait long enough?)
-check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/XXXXXXXXXXXXXXXX does not exist. Dropping to a shell!
BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
(initramfs)[/b]

I have no idea what this prompt even means.  I then attempt to go back into the installer with a hunch that maybe I need to de-RAID my /boot file partition and set up an individual /boot on each SATA disk.  I boot the installer and ALL the previously configured partitions are gone.

I'm at a loss. I keep trying to do research on the web but most everything I can find is either far too technical for someone completely new to Ubuntu or does not apply to my set up as far as I can tell (coupled with the gross probability that I'm making numerous fatal mistakes).  I lost my Windows installation and my desktop is the only one in my five person household. My mother is nagging at me because she has to do her Farmville on my Macbook without a  mouse...and thus I plead my case here.  Can anyone help? If you have something for me to try that requires working from the (initramfs) command prompt you will have to give me step by step instructions as I have very minimal experience with any command prompt style systems & none whatsoever with Linux. Any help would be greatly appreciated.

---

### Post by WhiteyWan on 2010-01-14
*bump*

---

### Post by WhiteyWan on 2010-01-14
Since originally posting this in the other forum, I have tried a new installation with partitions configured such that all free space was at beginning of disk and the /boot partition is not a RAID partition. My /boot is a .ext3 file system (I changed the "Bootable Flag" to 'yes', which I think is necessary) that I mounted on the first SATA drive listed in the partition managing part of the installer. I'm assuming the first SATA drive listed would be the one that the system attempts to boot from by default but is this necessarily true? Regardless, I ended up with the exact same:
grub loading:
error: biosdisk read error.

Followed by what appears to be the Ubuntu loading splash (just a small white shape in the middle of the screen), and then: 

gave up waiting for root device. *Common problems:*
- boot args (cat /proc/cmdline)
- check rootdelay= (did the system wait long enough?)
-check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/XXXXXXXXXXXXXXXX does not exist. Dropping to a shell!
BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
(initramfs)

Any help for an Ubuntu n00bie?

---

### Post by WhiteyWan on 2010-01-14
New info:
After the 

grub loading:
error: biosdisk read error.

I am now getting a new error message:

udevd-work[123]: pipe failed: Too many open files

Not sure if this was coming up before but I just now noticed it...

---

### Post by proksy on 2010-01-17
I am new to ubuntu but not new to linux, I've been using some distro of it for over 7 years but I have become unbelievalbly fed up with grub2..I was trying to install ubuntu 64 on a raid 0 system..turns out grub2 doesn't work with raid, so I gave up and decided to go with the linux/software raid as you have.  I have also followed the instructions which appear to be for older distros of ubuntu and not 9.10, these instructions do not work.  I am also stuck in the exact same mud hole as you and have now completely lost the taste for ubuntu.  I really thought this could have been the greatest personal OS linux distro ever made..I now know I have been grossly mistaken..I'm sorry I don't have any answers for you and I hate to say but I don't think you will get any answers on this issue...I think we're up the creek w/o the paddle on this one.

---

### Post by proksy on 2010-01-17
As of now I am attempting my 13th go at installing ubuntu 64. I have tried partitioning both of my hdd's used as raid volume and each had a corresponding swap. This method allows the installation to complete unlike installing under a raid/fakeraid but upon completion and reboot the box fails to boot and leaves me at the initramfs prompt. I have tried partitioning a separate partition from the raid to have /boot installed on it, the installation completes but am brought back to the initramfs prompt. I then decided to scrap the idea of using two hdd's all together and physically removed one of my drives and reformatted, the install completed but was again brought back to the initramfs prompt. I have found a few threads that may lead us in the right direction but I have yet to have any success as I don't have internet capability, but you might so...
 
[http://ubuntuforums.org/showthread.php?t=1360445&highlight=initramfs+grub](http://ubuntuforums.org/showthread.php?t=1360445&highlight=initramfs+grub) >> fakeraid/raid
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) >> linux/software raid
 
I have tried the linux/raid link w/o any success but I hope this may help you.

---

### Post by WhiteyWan on 2010-01-17
Thanks for the reply. I ended up giving up on attempting to install Karmic and instead got the 9.04 distro, booted up perfectly.  Now my only question is if it's possibly to upgrade to Karmic without upgrading to GRUB2...

---

### Post by proksy on 2010-01-17
I am about to try that...the developers SHOULD have held back on the release of this until this was fixed...WHAT A NIGHTMARE!!!  I have found the problem I do believe...the problem is that this idiot, stupid, retarded, step in the wrong direction, grub2 boot loader is for whatever reason using the uuid of my floppy drive and associating it with my root device for /boot.  I have tried editing my commands to set root= /dev/sda, /dev/sda1, /dev/md0, /dev/md1...I am thinking I need to unmount my install drive and remount it, but if burning a copy of 9.04 saves me from pulling all my hair out then....Ya I'm going with 9.04 haha SCREW grub2 it sux...more testing before official release next time hopefully.

---

### Post by proksy on 2010-01-17
I do want to post my menu.lst and if anyone can give me some pointers on what to do I am all ears and willing to learn something here.
 
recordfail=1
if [-n ${have_grubenv}]; then save_env recordfail; fi
set quiet=1
insmod raid
insmod mdraid
insmod ext2
set root=(md0)
search --no-floppy --fs-uuid --set 7ead298c-f574-4328-ab3e-95rd994364eb
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=7ead298c-f574-4328-ab3e-95rd994364eb ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
 
errors:
 
mount: mounting /dev/disk/by-uuid/7ead298c-f574-4328-ab3e-95rd994364eb on /root failed: Invalid argument
 
/sys failed: No such file or directory
/dev failed....
 
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.
 
I am certainly not giving up on this so ANY help figuring this out is GREATLY appreciated as I have other machines that will need to have ubuntu 64 on them.  Once I figure this out I will basically image the hdd and start cloning this 9.10 distro but as of now I'm going with 9.04.  Major Thanks in advance :)

---

### Post by proksy on 2010-01-17
as a work around for this I have found that if one goes to the super-market and buys a usb wireless card internet from a neighbor can be "borrowed" and uninstalling grub2 and reverting back to grub seems to be the easiest possible way to get this going other than installing 9.04 which I've done, but those threads earlier do work...you may have to go through it more than once as I ran into some snags but those are Great! Nice work

---

### Post by WhiteyWan on 2010-01-18
Yeah, I've got my first Ubuntu boot going now on this 9.04 and I like it.  I suppose I'll just wait for the next release when hopefully they have the GRUB2 kinks worked out.  Which then begs the next n00b question: Can I upgrade directly to the next release or will I have to go up to 9.10 first?

---

### Post by gilson585 on 2010-01-23
You can upgrade directly to the newest release though it is typically better to do a fresh install. If you back up your home directory and restore it latter you won't lose anything except any extra packages you installed wont be there. On another note you can revert to legacy grub after installing 9.10 karmic. I have put together a how to after having issues with my stripped raid array. I don't blame you if you don't want to do it after fighting it for so long. link here [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445) On another note some users with a mirrored setup have unsuccessfully installed it using these instructions. It's safe to assume it works on stripped arrays when the raid controller is configured. I'll be adding this to the wiki as soon as I remedy the Raid 1 config.

---

