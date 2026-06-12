---
title: "dual boot win7 partition problem"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by elektra on 2010-10-29
I've just got a new laptop - an HP Pavillion dv7_4035sa with 500GB HDD - and I'm trying to set up a dual boot with Ubuntu 10.04.

I've used the windoze tools to create Recovery disks and there's nothing on the hard drive that needs backing up because it's brand new. 

I've run into problems with the partitioning. Obviously, I want to keep the windoze OS so I can't just erase and use the whole disk when installing Lucid but there was no option to 'install alongside' on the LiveCD. So I used the windoze disk management system to shrink the win7 partition, which left me with unallocated space (about 219GB). Booted back into the LiveCD and found that I couldn't use the unallocated space so booted back into windoze and formatted the unallocated space as ntfs. I realise that this is probably where I made a massive mistake but I don't know how to fix it. 

Booted back into the LiveCD and found that I could indeed format the new volume partition but I can't create a swap partition, and frankly the partition table just doesn't look right. So I haven't proceeded any further until I get it figured out. 

Under Windoze I can see 5 partitions (screen shot attached, ignore the Corsair one, that's an external)
but under Gparted on the livecd I can only see 4:
 
sda1 - unknown - system - 992.50KiB
sda2 - NTFS -  ----           -  199.0MiB - boot
sda3 - NTFS - New Volume - 223.57GB
sda4 - NTFS - Recovery -     242.00GB


which doesn't match what windoze shows at all, hence why I'm confused. I'm guessing that the New Volume is now the win7 and unallocated space combined? Before I started mucking around with this the partition table showed a Recovery partition of 22.1GB, a FAT32 partition of 99MB which is the HP Tools section and a system partition of 199MB, the rest of the disk was the win7 partition, which is the bit I resized. 

To complicate matters this laptop has something called HP Quickweb, which shows up upon boot before you get to the windoze splash screen. It's great because it allows you to access the web and a few other things without resorting to win7 OS but I can't figure out where it's stored on the HDD, or whether it's gonna complicate the installation of GRUB2. Anyone else had to deal with this before?

Any ideas on how to proceed with partitioning the HDD? I really want to leave the win7 stuff alone and I don't mind deleting the HP Tools section because I've taken a backup of it. Any help at all would be greatly appreciated

---

### Post by elektra on 2010-12-02
in case anyone else runs into this: 

the actual problem I ran into is that during all the mucking about I did with partitioning, Windoze rather helpfully converted my basic disk to a dynamic disk, meaning that I couldn't do anything else with it. Typically Windoze did this with inadequate warning (either about what it was about to do or the consequences of said action) and has no built in system for changing the disk back to a basic disk without a lot of effort and losing all your data. However, I did finally find a way out of the mess I got myself into and managed to restore the HDD to a usable basic disk by doing the following:

back up your stuff, this will wipe your entire HDD, and make sure you've made Windoze recovery disks. If you haven't, make them before continuing, without them this will not work.

delete your recovery partition and the HP Tools partition. Boot into the Recovery disks and select 'restore to factory settings'

once it's complete (it'll take ages so be patient) your HDD will be back to being a simple disk. Update your Windoze OS and create a dual boot.

---

