---
title: "After installing 16.04, selecting Ubuntu partition takes me to Windows (dual boot)"
date: 2017-01-12
forum: Installation &amp; Upgrades
---

### Post by shlady on 2017-01-12
So, I'm using an Acer Aspire E5-575G-53VG. I had it dual booted with 16.04 and Windows 10. I was trying to get some stuff installed and having issues with all the dependencies and, with only a few hours of work on it, I decided to just do a fresh install. When I installed it, I restarted and selected the Ubuntu partition. However, each time I do, it just takes me to Windows. I'm not sure what changed and wondering if anyone has seen this before.

Thanks to oldfred for the great response. It was changing the trusted EFI file. I had done it on the past install but it was a different grub for this new install.

---

### Post by oldfred on 2017-01-12
Are you installed in UEFI boot mode?
Did you set the UEFI supervisory password and enable trust on the ubuntu/grub .efi boot files. This is unique to Acer's UEFI.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 


 Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) 

Older threads mention downgrading UEFI, but newer one say newest UEFI from Acer works, so best to make sure you have newest UEFI from Acer.
      
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
           
 Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

