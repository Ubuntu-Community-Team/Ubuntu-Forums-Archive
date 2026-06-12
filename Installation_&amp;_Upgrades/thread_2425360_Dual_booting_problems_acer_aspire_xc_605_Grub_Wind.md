---
title: "Dual booting problems acer aspire xc 605 Grub Windows 10 Ubuntu"
date: 2019-08-24
forum: Installation &amp; Upgrades
---

### Post by mrjake-thompson-23 on 2019-08-24
Ok so I'm using an acer aspire xc 605, I have windows installed on my main hdd and decided I wanted to install Ubuntu on a different hdd so I followed all the normal install procedures however after I installed and restarted It gave me no Grub menu to select which system to boot into. I'm also not seeing an option to boot into my ubuntu drive in my boot options. I've seen alot of people having issues with this process on Acer machines but haven't been able to find a fix.
also my bios mode is UEFI


Any help would be great.

---

### Post by oldfred on 2019-08-24
Acer requires UEFI update and if SSD, SSD firmware update.

All Acer seem to need you to set "trust" from within UEFI on the Ubuntu UEFI boot entry, which is unique to Acer.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator) 
    
If only booting from internal drive that is all you need.
But if you want to boot from external drive, you may have to reinstall.
Ubuntu's Ubiquity installer has a bug (very old) that only installs grub to first drive. Selection on Something Else partitioning screen does not make a difference.
And you must partition in advance to include an ESP - efi system partition on the external drive.
UEFI only directly boots external devices from ESP & /EFI/Boot/bootx64.efi. Grub now does create that file, but you have to add it yourself. 

You can do a work around, I posted in bug report. Or you can copy /EFI/Boot & /EFI/ubuntu from internal drive's ESP to externals drive's ESP, or you can reinstall grub, often easier with Boot-Repair's advanced mode to select install & drive.
A full install's grub version of /EFI/Boot/bootx64.efi has internal file/path set to find more files in /EFI/ubuntu so both folders required. 

       Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by mrjake-thompson-23 on 2019-08-25
Thanks I have seen some of these posts and tried to follow however I'm unable to find the "Select an UEFI file as trusted for executing" option.

---

### Post by oldfred on 2019-08-25
You need to have Secure Boot on and set a UEFI password. Never lose that password or reset back to no password when done.
I do not have Acer, but thought some of the links gave enough details. They all are similar but some give a bit more info than others.

---

