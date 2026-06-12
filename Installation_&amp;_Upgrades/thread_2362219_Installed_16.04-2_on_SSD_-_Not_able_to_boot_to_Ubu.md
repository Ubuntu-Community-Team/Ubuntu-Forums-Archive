---
title: "Installed 16.04-2 on SSD - Not able to boot to Ubuntu"
date: 2017-05-25
forum: Installation &amp; Upgrades
---

### Post by philtsmith570 on 2017-05-25
Forum,

I just added a Samsung SSD to my laptop (Acer E5-575-52JF).  After partitioning and getting Windows booting off of it, I deleted all partitions from the old internal hard drive.  I then installed Ubuntu 16.04-2 on the 100 GB SSD partition (New drive).   After rebooting Ubuntu loader didn't come up.  Checked the BIOS.  There are four Ubuntu related boot options before the new SSD drive and Windows loader.  These are the same as when I was running the Ubuntu 16.04-1 off of the internal Hard drive.  

I rebooted and ran F12 for the Acer boot menu and chose the first one ubuntushimx64.  Boots to Windows.  

Downloaded boot-repair off a live usb and ran.  Rebooted and all is still the same.  Boot-repair didn't solve the issue.

Tried rebooting and holding the SHIFT key down to check if the loader would come up.  Just boots to Windows 10.

Any ideas, thoughts, opinions?

Best regards,
-phil

---

### Post by oldfred on 2017-05-25
UEFI boot?
On Acer?

Acer has a unique requirement with UEFI boot, that you have to set a supervisory password in UEFI and enable trust from within UEFI on .efi files in the ESP - efi system partition.
Some with e5's have posted that they had to downgrade UEFI. But then newer posts say the upgrade to very newest UEFI works. So make sure you have newest UEFI from Acer.

       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[URL="https://ubuntuforums.org/showthread.php?t=2342323"]https://ubuntuforums.org/showthread.php?t=2342323
[/URL]
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
      
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    
Also if new drive, with new ESP - efi system partition the entries may not be correct in UEFI.
post this, GUID in efibootmgr & drive must match:
sudo efibootmgr -v
       to see GUID/partUUID for each device sda and sdb, post with code tags to preserve formatting:
lsblk -o +PARTUUID /dev/sda

---

