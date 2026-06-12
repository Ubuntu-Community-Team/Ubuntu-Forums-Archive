---
title: "Installing 11.10 on Lenovo S205."
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by chipist on 2011-10-31
I have a Lenovo S205 (AMD E350 APU) netbook. I would like to install Ubuntu of some sort on it. It came with FreeDos installed, which on my 1st attempt to install Ubuntu I used the whole disk.
 
Having read some other posts (mainly in German), it seems that The EFI (BIOS) in the S205 does not work with GRUB2 for a Linux only install.
 
Here are the steps I have taken
 
1) Boot from live USB stick.
2) Run gParted, remove all partitions, then create new boot table (msdos)
3) Create 4 new partitions, 
1 - 200MB EFI boot partition
2 - 80GB /
3 - 200GB /Home
4 - 8GB SWAP
 
(PS, do these need to all be primary partitions, or can some be logical?)
4) Run the installer from the the live USB session
5) Assign the partitons as above (the / and /Home are not assigned during install)
6) Complete install (not sure if I get a failure at this stage when it gets to the installing GRUB2 part late on in the install process, although this may have been with previous version or mint or something)
7) When installl is finished, open a terminal
8) mount the / partiton, bind /proc etc and chroot . so that I can install GRUB instead of GRUB2 to the hard drive and not the USB.
9) Purge grub-pc to remove GRUB2
10) apt-get install grub.
 
At this point it tells me that there is no GRUB in the repositories. Can someone confirm that this is true? If so can I get a copy of the .deb from 11.04 or something and install it? Will this cause a problem. Or is there any easier way to get any recent version of Linux installed on this machine? It have been trying for weeks to get this sorted out now, I am currently booting from a USB stick so that I can use it!

---

### Post by zvacet on 2011-10-31
According to [this]("http://packages.ubuntu.com/oneiric/grub") lagacy grub is in repos.If you want to you can download package from that site ( look at the bottom to choose your architecture).Also maybe it is good to read [this.]("https://help.ubuntu.com/community/Grub2#Reverting_to_GRUB_Legacy")

---

### Post by chipist on 2011-11-02
OK, finally got 11.10 64bit to boot. :)
 
The following are for a full disk install, not dual boot on said Lenovo S205
 
1) On another PC, use unetbootin to create a bootable 11.10 USB stick (Mine was 2GB)
2) Stick bootable USB stick into one of the right hand USB slots on Lenovo S205
3) Switch on S205, hit fn-F11 several times as it boots (fn-F11 = F12).
4) Select USB stick from boot menu
5) The screen will be a mess, but just hit enter and you should boot into 11.10 desktop
 
6) run gParted
7) Delete all existing partitions (select each one, right click, delete)
8) From the menu, select create partition table (I think), and click OK, this creates a DOS partition table
9) Create 4 new PRIMARY partitions as follows
  sda1 fat32 200MB
  sda2 swap 8000MB
  sda3 ext4  80000MB (This is a bit large unless you intend to install a lot of software)
  sda4 ext4  what is left MB
10) Apply the changes then close gParted
 
11) Start the Ubuntu installer from the desktop
12) When you get to partition screen, select something else
13) assign the sda1 as EFI boot
12) swap will still be swap
13) assign sda3 as EXT4, mount point /
14) assign sda4 as EXT4, mount point /home
15) click next and go through the full install process, with ethernet cable attached for internet connection.
16) Reboot.
 
This worked!
 
Now a few notes.
1) I tried to do this from a USB CD drive with a LiveCD but it would not boot, I would just hang at the scrolling red and white dots on the Ubuntu boot screen.
 
2) I tried the above many times, as I got several kernel panics when trying to install for no obvious reason and other freezes.  Keep trying and hopefully you will get there eventually!
 
3) I have read elsewhere that you needed to install GRUB not GRUB2 by mounting and binding the hard drive /proc etc.  I did not need to do this.  Maybe because the ethernet cable was plugged in that it removed GRUB2 and used GRUB-EFI or something?  At the start of the install process I did NOT check the download updates box (I did for the mp3 one)
 
I could not install the latest ATI driver, but there were 2 options in restricted drivers and the older ATI driver worked.  A 2 monitor setup worked fine (netbook screen and 1080i LCDTV via HDMI).  The sound also worked over HDMI cable.  Change source in audio settings for the output tab.  This part was much easier than I expected!  Not sure hardware accelleration is working though, well not for flash anyway, again I need to look into this.
 
Mousepad working fine, audio fine, not tried USB and SD card ports properly yet.  Closing the lid it went into suspend mode fine.
 
Ethernet was fine, Wireless not working, can not even swtich wireless networking on.  I have seen in other threads about this though so will investigate further.
 
I hope this helps someone else, as there is not that much info around for this in English.

---

### Post by parovelb on 2011-12-01
I have tried installing through winxp and pendrive and unetbootin, then again through a linux made startup flash drive. I have also tried the "delete ui" method and the grub2 downgrade method without success.

Your post helped me. Thank you!

It's alive!! :twisted:

---

### Post by davebriggs on 2012-03-04
Hi there

I am trying this but failing pretty early on - I can't delete the partitions already created by Ubuntu /dev/sda2 (extended) and /dev/sda5 (linux-swap) in gparted  - perhaps because their status is set as 'busy'?

Any ideas?

Thanks

Dave

---

### Post by oldfred on 2012-03-04
Thread closed, it is an old thread. Another newer thread.
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)

Dave Briggs, if you have issues best to start your own thread. But you do have to use a liveCD verions of gparted or Ubuntu liveCD that has gparted. Then partitions are not mounted. Often liveCDs automount swap so if you have a swap on the hard drive you may still have to swapoff to unmount it.

---

