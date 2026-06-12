---
title: "error: no device found grub rescue"
date: 2013-03-12
forum: Installation &amp; Upgrades
---

### Post by arneckelmann on 2013-03-12
Hi,

I originally had Windows 7 on my computer and have recently tried to partition my hard drive and install the latest version of Ubuntu. After installing it, I tried to restart the computer without the live CD and it gave me the error stated in the title. I've tried using BootRepair to see what the problem was and got this output: [http://paste.ubuntu.com/5608899/](http://paste.ubuntu.com/5608899/)

I then did some Googling and came across this link:
[http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue](http://askubuntu.com/questions/143667/boot-error-no-such-device-grub-rescue)

I followed the instructions of the highest rated comment. I followed them verbatim.

After restarting the computer again, I now have this displayed:

GNU GRUB version 2.00-7ubuntu11
Minimal BASH-like line editing is supported....

I feel like I have made the problem only worse and don't know what commands I should try to execute.

Thank you for your time.

---

### Post by presence1960 on 2013-03-12
Ubuntu is not installed. Your hard disk (250 GB) has two NTFS partitions. They are your Windows installation. Whatever you did something went wrong. Boot the ubuntu Live CD/USB and "try ubuntu". When the desktop loads open a terminal and run ```
sudo apt-get install lilo
```
This will install lilo to the live ubuntu session. next in termainal run ```
sudo lilo -M /dev/sda mbr
``` This will put a generic windows bootloader on your MBR so you can boot windows again. Reboot without the ubuntu CD/USB. You should boot to windows, provided that whatever went wrong didn't mess up windows.

From Disk Management in windows shrink your C: partition to make unallocated space for Ubuntu. How much space to shrink depends on what you want to do. If you want just a basic install with ubuntu ( / ) and swap about 10-16 GB should be fine. If you want a shared data partition for ubuntu and windows to read/write to then add space accordingly. If you are adding a shared data partition then when ready to install boot the Ubuntu Live CD/USB to desktop again and use gparted to make an extended partition from the unallocated space. Then inside the extended partition create a swap partition equal to your RAM. Then create an ext 4 partition 10-14 GB for ubuntu. The rest make an NTFS partition for your data. Now install ubuntu. You will choose "Something else." Highlight the ext 4 partition for ubuntu and click "Change." Select " / " as mountpoint, make sure ext4 is selected as use as. Continue with the install. If you don't want a shared NTFS data partition just create " / " and swap as above and do the install.

**_Always have a working back up of your files before starting any partitioning/installation operations!!!_** As you have just witnessed sometimes things don't go as intended. Hopefully your windows installation is still bootable.

---

### Post by presence1960 on 2013-03-12
I should have asked this first...Do you want a dual boot with windows or do you want to wipe windows and have only ubuntu??

Is your machine using BIOS or UEFI?

---

### Post by arneckelmann on 2013-03-13
> **presence1960 said:**
> I should have asked this first...Do you want a dual boot with windows or do you want to wipe windows and have only ubuntu??

Is your machine using BIOS or UEFI?

I wanted a dual boot. I followed your instructions and everything went smoothly. Thank you so much!!!!!!!

---

### Post by presence1960 on 2013-03-13
> **arneckelmann said:**
> I wanted a dual boot. I followed your instructions and everything went smoothly. Thank you so much!!!!!!!

You are welcome!! Enjoy Ubuntu.

---

### Post by Chok182 on 2013-05-17
Hello i'm kinda of a noob at this at all. I tried to install ubuntu 3.04, i have put it on a cd and it worked fine a t firs, the installation process was okay, but then when it restarted and i took the cd out, it says no device found grub rescue, then i decided to put the cd back and it worked, and asked Install ubuntu or try now? I tried to install it again but it didn't help, My friend told me to press any key an F on it so i did, An option showed SA"something" and another SA"something" he told me to choose the first one so i did, But it said no possible BIOS found :(( Pls help and 

sudo apt-get install lilo 

din't worked out for me, it said "dpkg was interrupted you must manually run sudo - dpkg ---configure -a' to correct the problem. PLS HELP!!!!!

---

