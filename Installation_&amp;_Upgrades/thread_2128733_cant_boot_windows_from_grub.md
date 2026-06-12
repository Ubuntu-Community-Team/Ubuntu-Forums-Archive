---
title: "cant boot windows from grub"
date: 2013-03-24
forum: Installation &amp; Upgrades
---

### Post by sparkie172 on 2013-03-24
hello, i have a acer s3-391 i installed 12.10 to dual boot by reading different threads.
when ubuntu boots i get grub which ubuntu boots fine. windows has two lines which i get a black screen with just some info saying error.
cant remember what exactly. my laptop is uefi with secure boot on both os boot fine. i just have to move the one i want up in the bio boot order. 
i have tried boot repair a coulple time with no luck. here is the last time i used it. [http://paste.ubuntu.com/5642374/](http://paste.ubuntu.com/5642374/)


thanks in advanced for any help

---

### Post by Virtuality314 on 2013-03-24
It might help to post the error you get when you try to boot in to windows.

---

### Post by sparkie172 on 2013-03-24
here is a picture of the grub screen
[https://www.dropbox.com/s/xdqfllbjwimppru/IMG_20130324_074221.jpg](https://www.dropbox.com/s/xdqfllbjwimppru/IMG_20130324_074221.jpg)
here is a picture of the error
[https://www.dropbox.com/s/j9n2ght7ddkse92/IMG_20130324_074253.jpg](https://www.dropbox.com/s/j9n2ght7ddkse92/IMG_20130324_074253.jpg)
both options for window give this error
gotta go to work. let me know if more info would help 
thanks

---

### Post by Virtuality314 on 2013-03-24
Based on your error, I found this thread:

[http://ubuntuforums.org/showthread.php?t=2102337](http://ubuntuforums.org/showthread.php?t=2102337)

Also, I'm not sure but this might help:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2013-03-24
I do not see anything wrong.
A bit unusual in that you have / in the SSD. Was this an UltraBook with Intel SRT? And is that turned off?

Some others
 Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

Some systems only boot with secure boot on. Some also have modified UEFI to only boot the Windows efi file.
      
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
I disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

      
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

### Post by sparkie172 on 2013-03-24
ok thank for all the replies. i got it to work.
i read the thread fred posted about boot repair.
first i disabled secure boot,then ran boot repair.
I then reset bios to default (had a couple of options that did nothing)
renabled secure boot. set ubuntu as 2nd in boot order after usb.
chose the fist option with windows in it got a recovery error .
then tried out the second option which booted to windows no problem.

again thanks for the help

this problem is solved:D

---

