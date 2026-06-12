---
title: "Installing Linux on second hard drive"
date: 2016-12-16
forum: MINT
---

### Post by halo07 on 2016-12-16
So we just got in a dell laptop at work that im setting up for a developer. It has a 500 spinning and a 256 ssd. It was set up to have the 500 spinning drive as the windows boot drive and the 256 ssd as a data drive. I am wanting to use the 256 for linux mint. 

My problem is that linux is not seeing the 256 ssd. I pulled the 500 gig spinning drive as to not accidentally install anything on it.

---

### Post by Keith_Helms on 2016-12-16
What interface is the SSD using?  SATA or the newer NVMe?  I'd go into the laptop setup screens at boot just to verify the hardware sees the SSD.  I recently built a new desktop system and I had to go into the boot order screens and tell the system to boot from the optical drive using uefi in order to get the install disc running in the correct mode.

---

### Post by oldfred on 2016-12-16
Moved to Mint sub-forum.

Is system UEFI or BIOS?
Best to have second drive in same boot mode.

But with UEFI it is a bit more difficult. You must use gpt partitioning for drive, and be sure to include an ESP - efi system partition even if not immediately used.

And grub only installs to ESP on drive seen as sda. If drive is internal then that is ok, but if USB external lots of reconfiguration required.

Post this:
sudo parted -l

What model Dell?
Is it using RAID? Desktop installer does not really work with RAID.

---

### Post by halo07 on 2016-12-16
so windows sees the 256 drive just fine. its one of the m.2 msata drives thats longer than the typical msata drive. I removed the 500gig primary drive and for some reason it still is not showing the 256 when im trying to install mint

---

### Post by sudodus on 2016-12-16
You can try with some other linux distros, for example Ubuntu ;-) The linux distros boot in slightly different ways and might have different hardware drivers. The m.2 drives are rather new, so it is also a good idea to try a new version of the linux distros (as new as possible, maybe even a development version, even if it there is a risk that some not yet tested upgrade will break the system).

---

### Post by oldfred on 2016-12-16
Is this also the new NMVe drive?

Best to partition in advance with gparted.
       gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)
Filesystem support
[http://ubuntuforums.org/showthread.php?t=2318570](http://ubuntuforums.org/showthread.php?t=2318570)

But the RAID setting will cause issues & leaves RAID meta data on drive. If you can/want to remove RAID, then you have to remove the RAID meta-data.
       
 XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241) 
           
 Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 8900 i7-6700 pcie_aspm=off (also: Asus X555UB)
[http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive](http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843) 
           
 Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241) 
    
       
 Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)

---

