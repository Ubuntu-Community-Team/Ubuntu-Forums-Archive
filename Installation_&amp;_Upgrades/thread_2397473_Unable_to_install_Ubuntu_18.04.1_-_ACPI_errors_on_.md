---
title: "Unable to install Ubuntu 18.04.1 - ACPI errors on X299, 7820x, 1080Ti"
date: 2018-07-30
forum: Installation &amp; Upgrades
---

### Post by x86frodo on 2018-07-30
Hello,

I am trying to install Ubuntu (18.04.1 for Tensorflow)  with no luck... and tried all its variants (Lu, Xu, Ku...),  and all other distros(Fedora, Debian, etc)...

I always get stuck after entering the "Try mode" with ACPI errors and system freeze.

[LIST]
[*]ACPI BIOS error (bug): failure looking up 
[*]ACPI error: Method parse/execution failed 
[/LIST]
 
I searched for solutions and tried:


[LIST]
[*]Boot from - usb stick, cd 
[*]BIOS update - already at the newest version 
[*]BIOS setting - fast boot, hyperthreading, turboboost, leagcy mode... 
[*]GRUB mod - acpi =off,   intel_pstate=disable 
[/LIST]
 
Config:

[LIST]
[*]intel 7820x 
[*]ASUS x299 gaming strix-e 
[*]128GB Adata 3000Mhz RAM (8X16) 
[*]Aorus GTX 1080Ti 
[*]970 evo ssd + 860 evo + bunch of HDD. 
[/LIST]

---

### Post by oldfred on 2018-07-30
You may need firmware update on SSD.

With nVidia you will need nomodeset boot parameter to install & first boot or until you install nVidia driver from Ubuntu repository. You may want graphics ppa to install newest driver.
You may still need other boot parameters.

Issues are often common by brand, as UEFI is similar or just update for newer versions.
       Asus X299 Wired Internet issue, UEFI system clock
[URL="https://ubuntuforums.org/showthread.php?t=2395036"]https://ubuntuforums.org/showthread.php?t=2395036
      [/URL]
 Asus Prime Z270-A  Ethernet patch
[https://ubuntuforums.org/showthread.php?t=2351572](https://ubuntuforums.org/showthread.php?t=2351572)
Asus Z97 Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2298896](http://ubuntuforums.org/showthread.php?t=2298896)
Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu) 
    
With multiple drives, be sure drive is gpt partitioned, has an ESP, and particularly you have an ESP on whatever drive is seen as first, either sda, or NVMe0n1.
Only use Something Else install option.

---

### Post by x86frodo on 2018-08-01
Thank you!
That was the solution. 

1. on booting editing the GRUB option - setting the **nomodeset **parameter
2. in Ubntu downloading **nVidia **drivers via **apt **and installation
3. editing GRUB option and setting the nomodeset parameter premanent
4. restarting and up and running, at 16 threads (none locked at 100%), all storage available - nvme, ssd,

---

