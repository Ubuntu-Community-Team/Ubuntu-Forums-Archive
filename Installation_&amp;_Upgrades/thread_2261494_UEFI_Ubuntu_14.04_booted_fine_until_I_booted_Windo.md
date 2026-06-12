---
title: "UEFI: Ubuntu 14.04 booted fine until I booted Windows 8.1"
date: 2015-01-19
forum: Installation &amp; Upgrades
---

### Post by GapInTheClouds on 2015-01-19
Hello,

For a while dual booting was working well. After pressing F9, the UEFI menu would show up with two Ubuntu entries ('Ubuntu' and 'ubuntu') along with 'OS Manager' (ie. Windows). I could choose one of the Ubuntu options and it would boot nicely in to Ubuntu, then one day (potentially after a BIOS upgrade?) it stopped working. Now when I select Ubuntu it boots straight into Windows (specifically with the 'hp' logo on my laptop). I've followed the Ubuntu UEFI page and checked the following entries (Secure Boot: Disabled, Intel Rapid Start: Disabled) and also in Windows 8.1 (Rapid start (?): disabled).

Then I ran boot-repair and I could boot into Ubuntu again. Hurrah. So, after booting into Ubuntu several times, I needed to use Windows. Next time I tried to boot into Ubuntu, it was back to booting into Windows even though I'd chosen Ubuntu. I also tried the 'Boot from EFI file' option and tried loading \EFI\ubuntu\shimx64.efi directly and it boots into Windows. I've had a look around the forums, but I can't seem to find any solution. Any suggestions would be welcome. Here is my paste from boot-repair: [http://paste.ubuntu.com/9779276/](http://paste.ubuntu.com/9779276/)

Also, not sure if this is related, but I get a GPT partition error. I tried fixing that once using gparted and the computer didn't boot anymore (presumably it moved the boot partition or similar?) and I had to use the Windows recovery image DVDs to get the computer back up and running.

Many thanks.

---

### Post by oldfred on 2015-01-19
Boot-Repair could not mount most of your partitions, so it does not show much.

And you now have a bunch of /dev/mapper partitions. Did you turn RAID on in UEFI/BIOS? Should be AHCI mode for drives.

And that would lead to a lot of gpt partition errors. Windows may ignore some of that.

---

### Post by GapInTheClouds on 2015-01-19
Hello oldfred.

Thank you kind sir. Spot on! It is because the laptop has a 750GB HDD with a 32GB SSD and it was using the SSD as a RAID cache partition (using Intel Rapid Storage Technology). I turned that off and now it boots with no problems. So is there a way to setup a RAID cache partition as I had before without affecting Ubuntu? It did seem to speed up the laptop, so it would be nice if I could have that enabled. I guess I'd thought it should be OS independent as it happens before OSes are loaded.

Thanks again for your help.

---

### Post by oldfred on 2015-01-19
Some have posted that they re-enabled the Intel SRT.
Others were more Linux users and just used the SSD as / (root).

Some with larger SSD, found that only the amount of RAM was really used, so they had both the cache & a / for Ubuntu.

        Intel Smart Response Technology
[http://mjg59.dreamwidth.org/26022.html](http://mjg59.dreamwidth.org/26022.html)
For GPT systems, this needs to have a type GUID of D3BFE2DE-3DAF-11DF-BA-40-E3A556D89593. 
For MBR systems, you need a partition type of 0x84[2].
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)

This is now older. Ubuntu now works better with the RAID on the Intel SRT. It sees it correctly, but grub may not install correctly in all cases still.

 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

 Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)

 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

---

### Post by GapInTheClouds on 2015-01-20
Excellent! Many thanks for those links. I like the idea of using the SSD as a root partition although I'll try and get the cache partition working first.

Regards.

---

