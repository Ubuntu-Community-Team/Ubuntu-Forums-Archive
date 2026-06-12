---
title: "How to Remove Old OS's from Dual Boot and boot straight into new SSD"
date: 2015-01-06
forum: Installation &amp; Upgrades
---

### Post by vincej on 2015-01-06
Hi - I have a desktop where I have previously installed Ubuntu as a dual boot with Windows 7 on the HDD. 

I have today installed an SSD onto my machine and installed a fresh copy of Ubuntu 14 onto the SSD. 

I have set the boot order in the BIOS to boot first from the SSD. 

However, when I boot, it goes to the orginal boot loader where I can see the new SSD at the top of the boot order but I can also see the old Ubuntu and Windows 7 as boot options. I don't want this. 

I want to boot straight into the the SSD and entirely bypass the old OS's thus immediately loading the new copy of Ubuntu straight from the SSD. 

How do I achieve this ?? I could reformat the old HDD. I am nervous that if I do this then I won't be able to boot into anything. Moreover, it still has data on it which I would like to keep if possible. 

Many thanks !

---

### Post by kpatz on 2015-01-06
Temporarily disconnect the HDD, boot Ubuntu, run sudo update-grub, shutdown, reconnect HDD, boot.

---

### Post by vincej on 2015-01-06
Ok - that's great, it worked a treat. Thank you ! 

However, it is still first going to a boot loader where the old OS's are gone, but it still offers a couple of memory tests etc. It pauses for a number of seconds before moving onto boot to Ubuntu. 

Is it possible for it to boot straight into ubuntu, windows style, without first showing the boot loader ?

---

### Post by Elfy on 2015-01-06
You can remove memtest

```
sudo chmod -x /etc/grub.d/20_memtest86+
```

I'd not stop seeing the bootloader - what if you need to run recovery mode. Can make it hard to see that.

You could perhaps set the timeout to something like 1 or 2 seconds

Edit /etc/default/grub

Mine is set to 2 seconds

> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


After any changes to that file you need to update grub

```
sudo update-grub
```

---

### Post by Dennis N on 2015-01-06
Does the old HD still contain any operating systems? I infer from what you wrote in post #1 that it does.
> I want to boot straight into the the SSD and entirely bypass the old OS's thus immediately loading the new copy of Ubuntu straight from the SSD.

If there is no other OS detected when update-grub is run, I always assumed Ubuntu is then set to boot without showing a menu.  kpatz's advice on post #2 eliminated the other OSes from grub, so why does the menu show? I are missing something here. Maybe this happens only if none are detected when first installed?

In any case, running **sudo update-grub** in #4 will reintroduce OS entries if the old OSes are still on disk 1 and it has been reconnected.

Another way would have been to disable the OS prober in /etc/grub.d and then update-grub. Should eliminate the other OSes from the menu without disconnecting. Will the menu still appear? 

```
sudo chmod -x /etc/grub.d/30_os_prober
sudo update-grub

```

---

### Post by vincej on 2015-01-06
that makes sense !  

2 secs didn't work for me. for some reason it gave me only about .75 sec so I went to 5 secs. 

Ok - now that I have everything installed can I go to the old HDD and delete the old >Ubuntu and the Old win7 and also the old boot loader - ie just keeping the data files ? they are on NTFS and ext4 partitions.

---

### Post by Elfy on 2015-01-06
> **vincej said:**
> that makes sense !  

2 secs didn't work for me. for some reason it gave me only about .75 sec so I went to 5 secs. 

Ok - now that I have everything installed can I go to the old HDD and delete the old >Ubuntu and the Old win7 and also the old boot loader - ie just keeping the data files ? they are on NTFS and ext4 partitions.

No reason why you can't. 

But please ensure that grub is definitely installed to the SSD :)

I often do similar simply by booting the install I want to be controlling grub and then running 
```

sudo grub-install /dev/sda
sudo update-grub
```

Once you're sure - you can remove the old installs - keeping data as you wish.

---

### Post by vincej on 2015-01-06
Ok - just to be clear - installed ubuntu onto the ssd and so I am assuming that grub is installed there.. other wise is would not boot. but how do I make 100% certain ?

---

### Post by Elfy on 2015-01-06
> **vincej said:**
> Ok - just to be clear - installed ubuntu onto the ssd and so I am assuming that grub is installed there.. other wise is would not boot. but how do I make 100% certain ?

You could run the bootrepair - that'll show you exactly what's going on.

But I am constantly having to make sure where grub's installed here - running the dev version, the previous version and the LTS here - and the dev one get's pretty regularly reinstalled. I do the commands I posted from the install I want grub to live on. So you would boot with the SSD and run them (or boot repair)

Funnily enough I'm expecting an SSD this week - and this is exactly what I will be doing here.

---

### Post by kpatz on 2015-01-06
> **vincej said:**
> Ok - just to be clear - installed ubuntu onto the ssd and so I am assuming that grub is installed there.. other wise is would not boot. but how do I make 100% certain ?Whatever drive you boot from is the one grub (should be) installed on.

If you disconnect the HDD and can still boot your Ubuntu from the SSD, then you know for certain that grub is on the SSD.

---

### Post by oldfred on 2015-01-06
The concern is that when you install Ubuntu with any of the auto options, grub will be installed to the drive that is sda. That may not be the SSD. Drive order is determined by BIOS and is often based on port order plugged into the SATA ports on motherboard.

Best to confirm. Lots of detail with the summary report from Boot-Repair.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Or you can check:
If this is not the SSD, then you need to reinstall grub to MBR.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

      
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

Running the dpkg command is better than just a simple install to sda, as it resets the default reinstall location on major updates.
Simple install of grub to sda.
      
 sudo grub-install /dev/sda

---

### Post by vincej on 2015-01-06
great ! Many thanks ! One last question: can I remove the partitions from the HDD thus creating one disc gain ?? 

Also I noticed that the new Ubuntu install did not create a swap partition on the new SSD ... but then does that really make sense when I have 16gb of main memory ?

---

### Post by kpatz on 2015-01-07
If there is a swap partition on the HDD that's probably why it didn't create one on the SSD.  With 16 GB RAM you likely won't need it anyway.

You should be able to use gparted to delete the HDD Ubuntu partition and expand the Windows partition.  Or better yet, use Windows disk management.  I prefer using Windows tools to manage Windows partitions, and Linux tools to manage Linux partitions, things tend to be more stable that way.

If you delete the swap partition, don't forget to remove its entry in /etc/fstab.

---

### Post by oldfred on 2015-01-07
+1 on kpatz suggestions.

In general I prefer smaller system partitions and larger data partitions. But Windows typically requires a much larger system partition than Ubuntu.

---

### Post by kpatz on 2015-01-07
> **oldfred said:**
> +1 on kpatz suggestions.

In general I prefer smaller system partitions and larger data partitions. But Windows typically requires a much larger system partition than Ubuntu.X2.  Another thing I would do (if starting from scratch) would be to partition the SSD with 2 system partitions, one for Ubuntu and one for Windows, and then partition the HDD with 2 partitions for data (one Windows, one Ubuntu).  Install both OSes on the SSD.  Then both OSes can benefit from the speed of the SSD, and you'll have plenty of space for data.

---

