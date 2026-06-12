---
title: "Boot screen cannot be scrolled to Recovery or Memtest"
date: 2017-07-07
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2017-07-07
BIOS is set as UEFI and Legacy. I installed (physically) a new ssd. Unplugged what had been the former OS drive which was partitioned: /dev/sda1 (as /), /dev/sda5 (as /home). Installed 16.04.2 to the new drive with /dev/sda1 is / and /dev/sda5 as /home. Rebooted with old drive's cable re-plugged in. Power up takes a while, but OS boots into ssd.  Now FSTAB calls former /dev/sdb (new drive) /dev/sda

There is no Microsoft product on these devices and there has never been any. Only Ubuntu.

Now, maybe my GRUB got confused as both drives were (or are) /dev/sda. GParted balked at something, saying 4K not 512, but gave the option to ignore or cancel, and I ignored. 

```
# <file system>      <mount point>   <type>       <options>       <dump>       <pass>
#** / was on /dev/sdb1 during installation**

UUID=06a4d250-9b34-43e0-a0c2-2fbf80bcef78 /     ext4  noatime,errors=$
# /home was on /dev/sdb5 during installation

UUID=9deada4e-82ad-45fa-a1c6-a8e68d8b41f5 /home   ext4   noatime,default$
# swap was on /dev/sdb6 during installation

#UUID=dfa4cea0-9116-466c-b7fb-1c215400a08f none            swap    sw          $
/dev/mapper/cryptswap1 none swap sw 0 0

```

Also:
```
mark@Lexington:~$ sudo tune2fs -l /dev/sda
tune2fs 1.42.13 (17-May-2015)
tune2fs: Bad magic number in super-block while trying to open /dev/sda
Couldn't find valid filesystem superblock.
```


After more work fixing the new install, and several more sudo apt update-grub; caused by changing swappiness, setting TRIM, and other disc work (memory-brain freeze), the boot time time screen, which allows for selecting 16.04 or Recovery or Memtest will not find the keyboard's cursor keys. That is to say, I cannot scroll and select Recovery. After some more attempts at fixing this, the computer powers up into the screen where one enters one's password; even with the Shift key held down steady.

Do I need to reinstall the OS? A simpler solution would oblige me.

What is the correct nomenclature for the screen that times down to boot or allows for selecting Recover, Memtest, and of course, 16.04?

---

### Post by efflandt on 2017-07-09
You are looking for the grub menu. What type of keyboard do you have and how is it connected to your computer (USB wired, wireless with included dongle,?)? It appears that your keyboard might not be working at all during boot.

If you install Ubuntu and it is the only OS on the system during install, by default it does not display the grub menu. So with your other drive disconnected, the grub menu would not display and if for some reason your keyboard is not working during boot you cannot make it display unless you change something in /etc/default/grub and run "sudo update-grub".

I am just guessing that you just need to comment out the line (put # at beginning) about GRUB_HIDDEN_TIMEOUT, or at least that is what I did after installing Ubuntu on SSD as the only OS on a laptop and then moving the drive to my desktop PC which also has Win7 and Ubuntu 14.04 on another drive.```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```Ubuntu uses UUID to identify partitions, so it really does not matter if a drive gets switched from sdb to sda (or even sdg on USB) as long as you have UEFI or BIOS set to boot the drive you want to be the primary drive and you do not have cloned partitions connected during boot with exactly the same UUID.

You have not shown any info about your other (old?) drive, only the USB memory stick with live/install system and what I assume is your new drive. I am not very familiar with UEFI, so not sure what you mean by "BIOS is set as UEFI and Legacy." Systems that you want to boot should all use either UEFI or legacy BIOS, not mixed. And in this case it appears that you installed in legacy BIOS mode because you have no (FAT32?) efiboot partition.

Also **tune2fs** is for partitions, not drives and /dev/sda is a drive, not a partition. Not even sure what you are trying to do with that if booted from live/install iso on sda which is a non-writeable file system like CD/DVD.

---

### Post by Mark_in_Hollywood on 2017-07-10
Thnx for a response, efflandt, first of all. 

The keyboard is wired. And, once I get to the screen to input the password, the keyboard works without problem. The keyboard and/or mouse do not work until the password input screen is reached.

Commenting out the TIMEOUT brings up the Recovery menu rather than booting directly into password entry screen, but again, the keyboard is non-functional at that time. The amount of time the ssd takes to boot tells me something is wrong. I can put a liveusb thumb drive and boot and reach the virtual desktop faster than the ssd. I know this as before I plugged in the former boot drive the boot time to fully loaded desktop was inside of 60 seconds.

This motherboard is MSI 970 Gaming. I have attached the M/B's manual page about BIOS. The BIOS has two options: UEFI or LEGACY+UEFI. Before I bought this m/b, about 9 months ago, I wanted one which was able to boot without causing Linux/Ubuntu problems. (I'm not a skilled person at all at this computer OS install work). If you believe that I can change the BIOS to UEFI alone and that will solve this problem, that's just what I'll do, but first, please help me understand what I'm doing. FYI, all my data from /home is backed up on an external device which is powered off; so if there is a problem, I can always wipe the device and start over.

Lastly, I don't understand all these partitions. There is but one drive attached at this moment. It was partitioned /sda1 and is about 11 gig and for / while the other is /sda5 and is /home of about 210 gig. There is about 10 gig of unused space (over provisioning). There is no (or I didn't create it) /sda2 of 2.38 meg formatted FAT32. That's just making me crazy! Again, thanks for your help.

---

### Post by oldfred on 2017-07-10
With new UEFI and BIOS motherboards you have to select one way to boot and only use that.
But USB usually has two selections to boot, one UEFI:flash and the other Flash which is BIOS. Where flash is the name, label or brand of flash drive.
But then system may be set to boot in different mode than you selected to boot flash drive. And how you boot flash drive is how it installs. So make sure System boot matches flash drive boot mode.

So you must always boot in UEFI mode or always boot in BIOS/CSM/Legacy mode for consistency. And what ever mode you have chosen, must be that mode you always use.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

And in UEFI you may have setting for USB support and/or USB mouse & keyboard support. Make sure those settings are on.

With new UEFI systems, may  be best to use UEFI for better support than the 35 year old, but well known BIOS/MBR configuration. But depending on how you originally installed may not be worth the effort to change now.

      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by Mark_in_Hollywood on 2017-07-10
Thanks, Old Fred. Your help much appreciated.

This motherboard's BIOS has but 2 options for boot time. One is UEFI. Today, as a test, I set the bios to that and that causes the disc drives that have Ubuntu on them to vanish, as those drives are not UEFIs. The other BIOS option on this motherboard reads: Legacy+UEFI. That is the configuration that was used when Ubuntu 16.04.2 was installed. With that option selected, the BIOS sees and reads (defaults to) and shows **ALL** available boot devices, whether UEFI or not. That is, the BIOS then can hand off loading to the linux GRUB bootloader. I hope this clarifies this. 

On my BIOS screen, the bootable devices are listed across the top and can be moved around. I have put the flash drive (as MSI calls it) first, then the ATAPI dvd and third is the SSD. Then come the UEFI devices. The screenshot attached shows the way that BIOS deals with both UEFIs and legacy devices, but is not mine, as the screenshot was save somewhere on the 'net or some drive, but nobody knows where.

---

### Post by oldfred on 2017-07-10
My UEFI system will only let me save to a FAT32 formatted partition or flash drive. I have saved to the ESP - efi system partition, but the default mount in fstab with a full install prevents access.That may be for secuity, but I change it to allow access as that was how earlier Ubuntu installs were configured & I need access as I have to edit entries sometimes.

My Asus system would only let me boot in UEFI mode, if I set it to UEFI only. It had CSM and CSM or UEFI with UEFI first, but that always only booted in CSM/BIOS mode.

Not sure then why you would not see drives in UEFI mode?

I do keep SSD as first in boot order and totally hide some like network boot that I would never use, so system does not spend any time checking for that.

If you UEFI  boot in live mode can you then see all drives?
sudo parted -l

I also found it was important when building a system that hard drives be in first SATA ports with no skipping of ports. So first drive must be in SATA0. And even having DVD in middle of SSD & HDD caused issues. So drives first, then accessory drives like DVD next.

---

### Post by Mark_in_Hollywood on 2017-07-11
> If you UEFI  boot in live mode can you then see all drives?
sudo parted -l.

I do not have a UEFI device, as far as I know. My motherboard has the ability to see/use UEFI devices, but I have never used UEFI to my knowledge. In any event, all I'm trying to do here is create new UUIDs for the sda and sda1 and sda5 (no swap) and clean up power up time. The 4 screenshots of an earlier post are all from GParted in liveusb mode. Why there is a 30 gig remains a mystery. It's not on the ssd. I believe plugging in the former hdd and booting with both installed has confused fstab et alia, that there are multiple partitions on the device. There aren't.

---

### Post by Mark_in_Hollywood on 2017-07-13
By reconnecting the second drive, I believe GRUB may be confused. It wants to find either or both MBRs maybe? What can I do to fix this? Do I need to do a complete re-install or can I get the ssd new UUIDs, run update-grub and clean it all up?

---

### Post by oldfred on 2017-07-13
You should not have to reinstall, although if system is very confused it sometimes is the easier fix, if you have good backups.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Mark_in_Hollywood on 2017-07-13
Thank you again, Old Fred & Linux Support. I'm marking this solved for now.

---

