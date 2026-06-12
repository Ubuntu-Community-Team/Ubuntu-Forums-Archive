---
title: "HDD Upgrade and triple boot setup"
date: 2013-03-29
forum: Installation &amp; Upgrades
---

### Post by ads2996 on 2013-03-29
Hi,

I have a friend from the States coming over to the UK sometime soon and they would be able to bring something small over with them. My plan would be a new hdd for my laptop. So my question is for my laptop which is a HP touchsmart TM2-1010EA. It currently has a 320gb 72,000rpm Sata Hdd.

1. 72,000 or 54,000rpm
2. 1tb or 750gb
3. I have 4gb of ram would 8gb be worth it
4. Would a triple boot of Win 7,Win 8 and Ububtu and a ntfs data partation be possible
5. If a triple boot is possible what sizes would u reccomend

Note A ssd is not a choice, as its too expensive and not large enough

thanks in advance

---

### Post by GeorgeLSpencer on 2013-03-29
Go for a USB drive, as you have no space internally in a laptop. I have triple boot on my desktop; but in my case each operating system is a separate disk (XP,Win 7, Ubuntu). Most external usb disks in Australia are now 1 or 2TB and I thought 7,200 rpm. If you are running 32 bit operating systems then you cannot use more than 4GB of RAM.

---

### Post by ads2996 on 2013-03-29
I already have an external 1tb usb drive, my problem is me and my laptop move about quite a bit. Also my current setup my c: drive 100gb and near full with none of my data on it. Does anyone know if there is a significance speed difference in 7,200 over 5,400. All the oses i would be running would be 64-bit.

---

### Post by darkod on 2013-03-29
A 7,200 should be faster than 5,400 but also more power consuming and heat dissipation. For that reason laptop 2.5" disks are mainly 5,400.

A triple boot is easily possible, and the total size you need depend on the size of your programs and data, only you know that.

If you want a triple boot with both win7 and win8 showing in grub, you need to move the boot flag before installing the second windows otherwise it joins the boot files and grub will show you only one entry for windows, which will then have a menu for both win7 and win8.
Best is to prepare the first windows partition from ubuntu live mode, put a boot flag on it. Install first windows.
Then create the partition for the second windows, move the boot flag to it. Install second windows.

That will make sure the boot files stay separate on its own partition. Grub will detect them and make two entries for win7 and win8 in the menu.

Also if your machine bios doesn't support booting from beyong 137GB you might need to have small 500MB /boot partition at the front, so it might be wise to leave 500MB in front and create /boot there when installing ubuntu. Just to make sure it will boot fine with a big 750GB or 1TB disk.

Don't forget msdos table has limitation of four partitions and windows needs primary partitions, so including a separate /boot you are probably looking at:
#1, primary, 500MB ext4, /boot
#2, primary, XXXGB ntfs, win7
#3, primary, XXXGB ntfs, win8
After that start creating them as logical
logical, XXXGB ext4, /
logical, XXXGB ext4, /home (for example)
logical, XXGB swap
logical, XXXGB ntfs (shared data)

EDIT PS. Creating the windows partition from ubuntu live mode in advance has another benefit. It saves you the small primary System Reserved partition that win7/win8 creates if you make partitions with the installer. Since you are planning to triple boot, even if you don't create /boot partition, it's not smart to waste primary partitions when you can easily avoid it.
If you don't like installing windows on ntfs partition created by ubuntu, you can format it again with the windows installer. The main thing is NOT TO create it using the windows installer, because that is when it slices off 100MB and creates the System Reserved partition. If the partition already exists and you format it, it doesn't do that. So, created partitions in advance = no small System Reserved partition.

---

### Post by ads2996 on 2013-03-29
Before I reformatted my laptop the c: drive was about 290gb, does this show it can boot beyond 137gb. My laptop already has a 7,200 drive would i best in keepung a 7,200 drive. I am glad a triple boot is possible. Would 8gb ram be beneficial?

---

### Post by darkod on 2013-03-29
Not sure, especially if you now have the System Reserved partition at front. That means the boot files are at the front. The 137GB limitation is not that it can't work with larger disks, it's that it can't use boot files beyong the 137GB mark. With two windows OSs in front, the ubuntu root partition will probably be beyond 137GB which means the boot files also. Even if the root partition starts before 137GB, you can't know where exactly the boot files will be saved on the partition, maybe at the back. Having /boot at front, makes it sure they are at front since they always go into /boot. It would take only 500MB which is nothing, and it could prevent many issues in future.

RAM is always beneficial. If you have single 4GB stick and you can add another one, great.

I added an EDIT in my previous post regarding avoiding the System Reserved partition. Read it, it can be very useful.

---

### Post by ads2996 on 2013-03-29
I see what you mean about the drive partationing. The laptop has two 2gb sticks atm. I am not sure if i would benefit from 8gb.

---

### Post by ads2996 on 2013-03-29
The cost for the parts are
750gb 7,200 £50
1tb 5,400 £50
2 x 4gb sticks £52

---

