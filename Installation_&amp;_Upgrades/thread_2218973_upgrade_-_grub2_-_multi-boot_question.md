---
title: "upgrade - grub2 - multi-boot question"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by malspa on 2014-04-22
I've always done a fresh installation rather than doing an upgrade from one release to another, but I'm thinking about trying to upgrade from 12.04.

I have 12.04 in a multi-boot set-up. I have Debian Wheezy's grub2 booting the other distros, with a custom grub entry for 12.04.

So, what will happen if I choose the upgrade path? I figure I'll have to re-do the custom grub entry, but will upgrading to 14.04 overwrite the MBR? Or will I be prompted before anything like that happens?

---

### Post by Double.J on 2014-04-22
Hi there!

well it kind of depends where you originally put grub? If you installed to the mbr, running update grub will re-write the mbr. If you set bootloader location to the partition, it will write to the partition and leave your mbr alone. That is if it even runs a full update grub - usually an update just modifys your systems grub entry.

in simple terms - what happens now when you get a kenel update in ubuntu? There's been several in the last couple of months, so if you've been staying up to date, it should go the same.

even if the mbr is overwritten by ubuntu, at the end if the day ubuntu will easily detect debian, and writing over the mbr entry will not affect any of your debian grub configs - you just boot into debian from the ubuntu grub and update grub from there and debian is back in charge of the mbr.

If it helps, a basic understanding is that the mbr is only 512 bytes of space (the first 512) on the hdd, so there's not a lot of space. For that  reason most of your grub is actually in /boot not the mbr: the mbr portion of grub is just there to recieve the boot process from bios and hand over to grub on it's partition. Whilst writing over the mbr means you don't have boot time access to the previous boot order, it doesn't delete the configs stored on that OS's /boot.

I have found with 14.04 that it detects more systems than most installers (inc opensuse), so I leave it in charge of the mbr. One thing to bare in mind - whichever OS is in charge of the bootloader on the mbr will only update the boot entry for itself. Say you are dual booting ubuntu and mint. Both recieve a kernel update and ubuntu is in charger of the mbr - next restart, ubuntu will boot the latest kernel, mint will boot the previous. You have to run an update grub to get the latest mint. 

Personally ly i use chain booting to get around all this nonesence - i install ubuntu to the mbr and each other OS specifically install grub to the / partition of that OS - it means I do have to go through two boot menus for all but ubuntu, not my mbr doesn't get erased and I always load the latest kernel.

---

### Post by kraanig on 2014-04-22
Hi
I am just dipping into linux and like the debian flavours I have installed mint 16 and played with it however I like the LTS idea and would like to replace the mint with lubuntu,
My current setup is dual boot win7 and mint what you saying is that I can install over mint (i presume through live) and then update the grub with the new installed grub(lubuntu), If I install over it will it still regornise the win7 or is will the new grub not regornise win7 anymore (even if you use something like bootfix or grub customizer afterwards) ?
However I am confused about your chainloader are you saying you load your first OS and from there you load your other ones ? is this also handy for me to preserve the win enviroment or should i not bother ?

---

### Post by oldfred on 2014-04-22
I used to use chainloading with grub legacy, but now just turn off os-prober and add my own entries into 40_custom. And you can boot the partition not the kernel with Debian based installs as they have a link to the most current kernel in /. 

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

If you have multiple installs each may want to reinstall to the MBR. Then Double.J's installs to partitions will prevent that or you can change location.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
If you unchoose everything then it will not reinstall or if you do choose a partition then it will reinstall to that partition. But never choose a NTFS partition, just the / partition for your install.

---

### Post by kraanig on 2014-04-22
Thanks or the info very interesting, still keeps one but in my mind that it will be dependable on one 'main' distro for a moment I thought grub was to be on his own as a start up but I presume you could use a 'tiny' distro wich use grub and that as the main for the bootloader so you can still change swap your working distro/windows behind it

again thanks for the info - food for thought (any change u know of a tiny distro that could function for the bootloader)
((Also as an extra thought on top is it still possible for this tiny bootloader to be encrypted and so 'protects' the grub ? and the subdistro's can the be encrypted as well for the main grub to read them ?))

---

### Post by oldfred on 2014-04-22
On my flash drives I just install grub2. But then there is none of the other parts of grub like os-prober so I have to manually maintain grub.cfg. I do add entries to also boot one or two installs on hard drive as emergency boot and boot ISO for installing.

I do not think you can encrypt grub. Windows 7/8 also has a separate Boot partition so you can encrypt the main install, but the Boot partition is not encrypted. 
But I think truecrypt installs its own boot loader for Windows.

 The Performance Impact Of Linux Disk Encryption On Ubuntu 14.04 LTS - std vs. full disk LVM or encrypted /home
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_encryption&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1404_encryption&num=1)

---

### Post by malspa on 2014-04-23
> **Double.J said:**
> in simple terms - what happens now when you get a kenel update in ubuntu? There's been several in the last couple of months, so if you've been staying up to date, it should go the same.

I think this tells me what I need to know -- thanks! I've kept up with the 12.04 updates.

I'm doing pretty well with grub2; I've got all-Linux multi-boot set-ups on three computers. I've just never tried to upgrade from one release to another. This should be interesting. Thanks to all for the replies!

---

