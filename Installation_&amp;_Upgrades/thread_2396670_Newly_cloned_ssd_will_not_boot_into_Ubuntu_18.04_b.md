---
title: "Newly cloned ssd will not boot into Ubuntu 18.04 but it will boot into Windows 10."
date: 2018-07-19
forum: Installation &amp; Upgrades
---

### Post by ddray on 2018-07-19
Hi, I am new to the Linux world and have made a successful installation of Ubuntu 18.04 on a couple of laptops. I have been loving it so far, but I have recently ran into a problem. I decided to upgrade my Dell Inspiron 7537 hybrid drive to a new ssd from Crucial. In the process I used an Inatek usb caddy and Macrium Reflect cloning software. When it was completed Macrium shows the two drives one on top of the other so we can see that the new clone has identical info and all looked good. So, I installed the new ssd and it will boot into Windows 10 immediately and completely bypass the Grub menu (old drive went straight to Grub and gave me the option for which OS I want to boot from).  Also, when I press f12 upon booting the boot menu will show Ubuntu, but when I click on it the system boots Windows instead. Furthermore, I decided to boot from the usb that I originally installed Ubuntu from (thinking of a fresh install) and I can get into the Grub menu. However, when I click on Ubuntu it will turn on the bootloader screen and instead of booting it will end with a black page that has some kind of failing text. I forget what the text says but I can come back and post it.

Update on black screen, 4 lines:
Couldn’t get size
Failed to set xfermode (err_mask=0x40)
Busybox v1.27.2 
(Initramfs) unable to find a medium containing a live file system.

---

### Post by TheFu on 2018-07-19
I would have used dd or ddrescue to clone a disk from A to B while booted from alternate media (aka a flash drive). This is a bit-for-bit copy.  The only reason I wouldn't do this is if the sector sizes for the 2 HDDs were different. That's usually 512b and 4Kb. Getting misaligned partitions has performance impacts on spinning disks.

If I needed to work at partition level rather than the whole disk, I'd use fsarchiver to clone each partition from A.  In the end, I'd have to run grub-install and update-grub to get the boot stuff put back correctly.

This assumes Dell follows the UEFI spec, which I think it does.  Not all vendors do and some need manual changes for UEFI boot to work.

Also, after cloning any disk, be certain to NEVER connect the original disk to the system as long as the UUIDs match.  Matching UUIDs can cause problems with mounts in strange ways.  There's a way to force new UUIDs on a disk/partition, but I don't recall how now.

Usually, someone else will post lots of links with relevant data about an hour after I post. ;)

---

### Post by oldfred on 2018-07-19
Not sure how Macrium would clone the Linux partitions. What is important is if UUID/GUIDs have changed or not.

Either way I would expect that you have to reinstall grub.
Many UEFI remove entries if drive is removed, but they often find the Windows entry automatically, but not any others.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by ddray on 2018-07-20
Thanks for chiming in you guys. So, I decided to put my original drive back into the Dell Inspiron (it works for Windows and Ubuntu), and I took the clone (ssd) out of the Dell and put it into a 2010 Macbook pro. Now, the clone works perfectly in the Mac (except no wifi connection for Windows) with displaying Grub first, and then giving me the option to boot from Windows or Ubuntu. Why does the clone work in the Mac and not the Dell?

I could just leave things as is and call it a day (except for the windows wifi issue), but I would prefer to get the clone working in the Dell since it's 4 years newer and a nicer laptop.

I hope this new info may shed any additional light on resolving the issue. If not, then let me know if any of the above info is something I should still look into. This is my first time cloning so I am not familiar with everything listed and will have to spend some time reading up.

---

### Post by oldfred on 2018-07-20
Most UEFI erase UEFI entries when a drive is disconnected.
And they seem to automatically find a Windows entry but not any others.
If cloned drive booted to Windows in Dell, then you probably need to just change boot order if there still is an Ubuntu entry or add an Ubuntu entry back into UEFI boot menu.

Check entries and boot order:
sudo efibootmgr -v
See also 
man efibootmgr

Boot-Repair report shows the efibootmgr info. And it would reinstall grub to add new entry if required.
You can manually add UEFI entry, but need to know which partition is ESP.
       sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number of ESP.

---

### Post by ddray on 2018-08-03
Is it possible to, "Check entries and boot order" if I cannot boot into Ubuntu 18.04?

---

### Post by TheFu on 2018-08-03
> **ddray said:**
> Is it possible to, "Check entries and boot order" if I cannot boot into Ubuntu 18.04?

Yes.  You would boot from a Live-Boot (flash drive or optical media), choose "Try Ubuntu", then access the storage that is part of the machine.  This is a good skill to have.  

In fact, with just a tiny amount of work (about 7 commands), you can boot from a flash drive and setup something called a "chroot" that runs everything, except the kernel, from any storage you want, even a non-booting machine.   From an environment like that, you can fix pretty much any boot issues.  It is also a way to totally hack any unencrypted computer. You can never be locked out just by forgetting a password.

---

### Post by ddray on 2018-08-04
Unfortunately, I have already tried booting from a live bootable flash drive, and when I click on "Try Ubuntu" it will go into boot mode with the Ubuntu logo but instead of Ubuntu coming on I will get what seems to be a busy box terminal. I wrote about this in my first post and listed what the terminal says. 

Are you implying that chroot must be used or is that a more advanced approach which provides multiple advantages?

---

### Post by TheFu on 2018-08-04
I'm confused.   How did you get Ubuntu installed? Wasn't a flash drive used?  Can't you do that again, but select "try ubuntu" when it boots? Are you using that same flash stick in the same USB port?  Until you get that solved, not much can happen.

There are lots of different solutions to reinstall grub and update the grub menu settings.  I only know the way I've done it, not every possible method.  Linux is extremely flexible. Each possible solution has pros and cons.  At this point, doing the easy method is all I got. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) is basically the goal.  Boot-repair, mentioned above, hasn't worked reliably for me. The link shows the terminal method, which has always worked for me, though I usually setup an OS chroot to do the grub-install and update.

---

### Post by ddray on 2018-08-09
I originally installed Ubuntu with a bootable usb. That worked just fine. Then, I switch out that hybrid drive for a new ssd that was cloned to match the hybrid exactly. Now, if I use the same usb on any of the ports (tried them all) Ubuntu shows up, but when I click on "Try Ubuntu" it won't make it pass the purple Ubuntu screen and then dead ends in what seems to be a busybox terminal.

---

### Post by oldfred on 2018-08-09
If a new computer it is UEFI.
Purple screen is BIOS boot mode. You want UEFI.
But what video card/chip? If nVidia, you probably need nomodeset boot parameter.
       
Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If a Dell you had to change drives from RAID to AHCI to install. But did you then update UEFI from DEll, which probably reset to defaults and you need to change UEFI settings again?
And you may have to change some USB settings for full access or allow boot. But I do not think you could start to boot.

---

