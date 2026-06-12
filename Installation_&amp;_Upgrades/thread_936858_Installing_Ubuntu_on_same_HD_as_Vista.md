---
title: "Installing Ubuntu on same HD as Vista"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by skozzy on 2008-10-03
I have read several posts of people having problems installing ubuntu when vista is installed. Is this still an issue ?

Recenty I installed Vista on a 320gig HD and I still have Ubuntu installed on another drive, so currently I use bios to switch drives to boot from.

But I would like to share the same drive and have ubuntu installed at the end of the drive and use grub to select Vista or Ubuntu so i don't have to keep changing bios settings all the time. Just to save 30 seconds of my life each reboot.

I have done it many times with XP and Ubuntu, but before I trash my Vista install on a test run, I just want to know if there is currently any issues running the ubuntu live cd to install ubuntu to a drive with vista running.

Currently I have ubuntu installed on a old 40gig drive (which has XP dual booting with grub), I want to remove it from the system to make way for a bigger HD .

---

### Post by c4tly5t on 2008-10-03
vista has a fancy partition manager that you can shrink your NTFS partition and free it up to ext3
right click drive C in my computer and find Manage and the partitioner is pretty easy and straight forward (like most MS stuff nowadays)

---

### Post by c4tly5t on 2008-10-03
vista has a fancy partition manager that you can shrink your NTFS partition and free it up for ext3
right click drive C in my computer and find Manage and the partitioner is pretty easy and straight forward (like most MS stuff nowadays)

---

### Post by caljohnsmith on 2008-10-03
If you can, it's definitely better to use Vista's Disk Management to do your partitioning and make room for Ubuntu; the reason is because Vista maintains its own partition table outside of the HDD's MBR (Master Boot Record), so if you use a partition editor other than Vista, it can break Vista since Vista's partition table will not agree with the new partition table in the MBR.

And just a thought, but you shouldn't have to switch which drive you want to boot from on start up just to boot Vista; just make the Ubuntu drive the first to boot, and then you can add a menu entry to boot Vista in the Grub menu. If you would like more specifics about doing any of this, let me know, otherwise let us know how it goes.

---

### Post by skozzy on 2008-10-03
[caljohnsmith] If you have a working solution i'm all ears.

I did add a menu entry to grub for the other drive to load vista but didn't work for me, I think cause Vista is installed on it's own drive a C: and when I switch drives in my bios reguardless of the chain order of drives the boot drive is always drive 0. So that makes vista or xp or win2k spit chips at me saying it can't find windows (all to do with the boot.ini file I think)

---

### Post by caljohnsmith on 2008-10-03
> **skozzy said:**
> [caljohnsmith] If you have a working solution i'm all ears.

I did add a menu entry to grub for the other drive to load vista but didn't work for me, I think cause Vista is installed on it's own drive a C: and when I switch drives in my bios reguardless of the chain order of drives the boot drive is always drive 0. So that makes vista or xp or win2k spit chips at me saying it can't find windows (all to do with the boot.ini file I think)
So do you want to stick with your current setup and get Vista booting OK from Grub? Or do you want to go ahead and shrink down Vista, and then add Ubuntu to that drive? If you want to do the latter, go ahead and do that; just make sure that when you get to the final stage of installing Ubuntu to the Vista drive, you click the "advanced" button and make sure you choose to install Grub to the Vista drive's MBR (Master Boot Record) by choosing /dev/sdX where sdX is the Vista drive (like sdb for example).

Or if you want to stick with your current setup and get Grub to boot Vista, please post:
```
sudo fdisk -l
cat /boot/grub/menu.lst
```
And let me know which NTFS partition is Vista. We can work from there. :)

---

### Post by skozzy on 2008-10-03
I will make a backup of vista first then try the partition resize and stick ubuntu to the end of the drive. If that works for me then I can remove the old 40gig drive and put in a bigger drive.

---

