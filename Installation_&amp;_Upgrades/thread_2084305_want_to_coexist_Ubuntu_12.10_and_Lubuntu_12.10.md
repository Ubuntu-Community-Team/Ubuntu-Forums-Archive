---
title: "want to coexist Ubuntu 12.10 and Lubuntu 12.10"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by riowg on 2012-11-15
Hi there, I've installed Ubuntu 12.10, but I now want to install Lubuntu side by side without removing Ubuntu partition.  

1, Can the default Linux Swap partition be shared?  
2, I knew about partition manager in Windows environment.  If my hdd space is scarce, is it ok to shrink Ubuntu Ext4 partition for Lubuntu?
3, How to install Lubuntu after having installed Ubuntu?  
4, But what boot manager do I need to install for this to work? 
5, I knew about multiple partitions and multiple boot for Windows, but I'm just new to Linux.

Thanks a lot!

---

### Post by darkod on 2012-11-15
1. Yes, the swap can be shared.
2. Don't use windows tools to shrink linux partitions. If you do have to shrink it, first make a full backup of all important data, then use the ubuntu live cd to boot into live mode and use Gparted to shrink it.
3. You can install lubuntu using the auto methods, or manually which I always prefer and recommend. Manually you can make sure you tell it to use the existing swap, if it does it automatically I'm not sure whether it will create new swap into the unallocated space or not.
4. Lubuntu will install its own grub2 but if you prefer to use grub2 from ubuntu, you can boot ubuntu once after the lubuntu installation is finished, and install its grub2 back to the MBR.

---

### Post by TenPlus1 on 2012-11-15
If you simply want to have Lubuntu and Ubuntu desktop managers as an option then you can pop into the software centre and install Lubuntu-desktop which will give you the choice of switching between Unity or Lubuntu at the login prompt...

If on the other hand you want separate installations then shrinking your ext4 partition and running Lubuntu live cd will let you install it alongside your standard Ubuntu installation and edit the grub menu to list them both on boot...  They will share swap...

---

### Post by riowg on 2012-11-15
> **TenPlus1 said:**
> If you simply want to have Lubuntu and Ubuntu desktop managers as an option then you can pop into the software centre and install Lubuntu-desktop which will give you the choice of switching between Unity or Lubuntu at the login prompt...

If on the other hand you want separate installations then shrinking your ext4 partition and running Lubuntu live cd will let you install it alongside your standard Ubuntu installation and edit the grub menu to list them both on boot...  They will share swap...

I want to speed up my netbook using Lubuntu.  Will the Lubuntu-desktop make Ubuntu run faster?

---

### Post by TenPlus1 on 2012-11-15
Definitely...  Installing Lubuntu-desktop and switching to that on the login screen will have you using OpenBox which is a very light window manager indeed...  Programs will load and operate quicker on screen, especially not having to use 3d-effects like Unity...

---

### Post by riowg on 2012-11-15
Thanks darkod and TenPlus1 for the explanations.  I've tried to install the lubuntu-desktop but failed with error.  I'm now trying to install Lubuntu alternate from scratch for the whole small ssd, but I met errors again...  Still struggling in the complicated installation... :(

---

### Post by darkod on 2012-11-15
The installation is not complicated at all, especially if you want to install on the whole disk. You can use the auto method that offers to erase and use the whole disk.

The manual install does require that you create the partitions yourself but i wouldn't call that complicated at all. You should know how to create partitions anyway if you want to optimize how you use your disk and plan it good.

Where are you getting stuck?

---

### Post by riowg on 2012-11-15
Many errors during installation.  At the first boot, logo comes, but screen is black afterwards.  Installation is just failed anyway.  Some say Lubuntu need user to mount point after installation.  I now may consider to install Xubuntu instead.

---

### Post by darkod on 2012-11-15
If there are errors during install you might have a bad cd (or bad image file that you used to burn the cd), or hardware issues with your hdd.

With many errors during install of course you can't expect it to work afterwards, it will not be installed successfully.

---

### Post by riowg on 2012-11-15
I'm now trying Xubuntu 12.10.  See if it works...  Thanks.

---

### Post by efflandt on 2012-11-16
I installed both Lubuntu and Ubuntu 64-bit 12.04 on 32 GB SD card with common /home partition for a netbook size tablet PC with detachable keyboard.   I had already partitioned the SD before that using gparted and used "Other" during install to chose what to put where.

The only issue I had during install is that I wanted to put Ubuntu's grub on its partition instead of the MBR and for some reason it would not let me (on my desktop PC I have 12.04's grub on a primary partition instead of mbr due to some Win7 programs overwriting grub2).  So Ubuntu on the tablet PC has no grub.

But other than that they both coexist and work fine using the same /home.

The only issue I had with Lubuntu is that by default it only installed alsa audio, which did not work (no PCM device in alsamixer).  But after I added pulseaudio, the PCM device appeared in alsamixer and sound worked (analog stereo).

Not sure what you mean by "Some say Lubuntu need user to mount point after installation."

---

