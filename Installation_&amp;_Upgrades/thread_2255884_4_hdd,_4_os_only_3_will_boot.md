---
title: "4 hdd, 4 os only 3 will boot??"
date: 2014-12-08
forum: Installation &amp; Upgrades
---

### Post by Andrew_Dennison on 2014-12-08
Problem one... I have tried to reinstall ubuntu 14.04 to a new 4rth SSD hard drive on my system, this was previously running on this drive and system FINE but was overwritten with a clean install using erase disk and LVM options from a live USB. Now this os will not boot, all other drives and OS will boot. boot repair fails and gives [http://paste.ubuntu.com/9427775/](http://paste.ubuntu.com/9427775/) 

Problem two... I need to replace drive 3 with old Ubuntu 11.10 for compatibility rollback with old applications. I have a live-USB with an iso from the old Ubuntu archives. This also will not install and boot. I have tried running it from the live-USB using the try option it doesnt work. I have tried installing it directly from live-USB and CD it doesnt work. The only way I have verified this iso file to work is installing in a Virtual machine with KVM and VirtualBox.

---

### Post by oldfred on 2014-12-08
Your multi-card reader consumes a bunch of drives, so I do not know which is which.
It looks like sda is your flash drive, and sdg is first real drive.

The grub in the MBR of sdh looks like it is set to boot system in sdg

But then your other systems are UEFI. Ubuntu only started supporting secure boot UEFI with 12.04.2. While 11.10 did have some UEFI support there were lots of issues and major improvements with each update to grub & kernels.

UEFI & BIOS boot modes are not compatible. Best if all systems are one or the other. Grub menu will only find (or work?) with systems installed in the same boot mode. Once you start booting in one mode you cannot switch. You can only switch from UEFI menu or perhaps one time boot key to choose drive/install. Some systems do require you to turn on/off UEFI or BIOS/CSM/Legacy boot mode to change method of booting.

Do not run any auto fix from Boot-Repair. It tries to install one grub to every MBR, Not sure with UEFI if it does the same or not. And it uses standard archives to update grub and make repairs so it will not work on obsolete versions. It should work on Precise, Trusty, Vivid, & Utopic. It looks like you were trying to update Raring or 13.04 which also is obsolete.

I do prefer to use gpt partitioning for both BIOS or UEFI installs. I converted my BIOS only system to use gpt with 10.10. And with 12.04 and a new SSD that I then thought I might move to a new UEFI system created both the efi for UEFI boot and 1 or 2MB bios_grub for BIOS boot partitions. All new drives I now partition with both, although with new UEFI system, I do not expect to use BIOS boot, but may want to test something so allocating 1 or 2MB is no loss.

Not quite sure why you should need an obsolete version of Ubuntu.

---

### Post by Andrew_Dennison on 2014-12-08
Hi thanks for your input. The reason we want to keep the obsolete Ubuntu version is that we have software that was compiled to run on Ubuntu 11.10 only, with a lot of developed applications and code for it. We want to roll back a drive for this, as was to compare against, while updating the applications and code to work with the latest software version running on Ubuntu 14.04. The same goes for the Ubuntu 13.04 install that was working fine until boot repair ran.

---

### Post by oldfred on 2014-12-08
Do not use Boot-Repair as it will only connect to current repositories. You need to install and connect to the archived repositories to get what updates were still there. That may not replicate the updated versions you did use will be part of the issue.
Those were probably BIOS boot? Particularly 11.10 as users had major issues trying to get it to work in UEFI mode. Some did.
Cannot really help any more on obsolete installs.

So if you have UEFI enabled, secure boot off can you select the ubuntu entry and boot? Or use one time boot key?

What brand/model/video chip computer or if you built it what motherboard?
Some brands modify UEFI to only boot UEFI entry with "Windows", so we have to work around that. 
And/or many systems have video issues and need boot parameters until proprietary video driver installed.

With multiple drives and multiple installs I prefer that each drive be configured with the grub boot loader on the same drive as the install. That worked well with BIOS, but on my system even when I told the installer for a test install, to put grub in my sdb harddrive, it installed to the sda efi partition overwriting my main installs boot. Or backup of efi partitions is essential.

Boot-Repair usually includes this, but I do not see it, post this:
Boot installer in UEFI mode.
       modprobe efivars
sudo efibootmgr -v

---

### Post by oldfred on 2014-12-09
thread closed. See this:
[http://ubuntuforums.org/showthread.php?t=2256005](http://ubuntuforums.org/showthread.php?t=2256005)

---

