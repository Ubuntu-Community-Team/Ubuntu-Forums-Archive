---
title: "Ubuntu installed, but grub2 won't boot"
date: 2016-11-30
forum: Installation &amp; Upgrades
---

### Post by jchubbs95 on 2016-11-30
Here is the paste bin: [http://paste2.org/WEZ89gHB](http://paste2.org/WEZ89gHB)
Yesterday, I received a new Acer Aspire S5 with Windows 10. I installed the latest version of ubuntu 16 LTS alongside windows. After the installation, grub won't boot, it just boots to windows like it normally did. I disabled secure boot and ran boot repair from my ubuntu usb, and even though boot-repair says it was successful, grub does not boot. This is part of the message that appeared after the boot-repair was "successful":

[I]If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi[/I]

I did all of that as well, and it still doesn't work. 

If it helps, before I installed ubuntu, I created three partitions:
/
/home
swap area

Please let me know if you need more information. I'm a noob when it comes to installing ubuntu, so any help would be very much appreciated!

---

### Post by oldfred on 2016-11-30
Acer is unique in that it requires you to set a UEFI supervisory password and enable from UEFI the .efi boot files in the ESP - efi system partition.
Some older threads many mention downgrading UEFI to older version to get it to work. But newer threads say newest UEFI from Acer works, so make sure you have newest UEFI from Acer.

These should be similar, but in explaining details may make more sense from one or the other.
 Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 
      
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392
[/URL]
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 


It looks like you installed grub multiple times. You may want to houseclean duplicates.
see also:
man efibootmgr
sudo efibootmgr -v
       
 Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B
Delete Ubuntu
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

---

### Post by jchubbs95 on 2016-12-03
Thank you for the response! Using the links you gave me, I found this thread that solved the issue: [https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 
Like gennarof mentions in the thread, I went to[COLOR=#000000] "Select an UEFI file as trusted for executing [/COLOR]in the BIOS, following the instructions, and it worked!

---

