---
title: "Problem detecting HDD and O/S on 9.10 install"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by lhcpr1 on 2010-02-20
Hello all,
 
Recently downloaded U9.10 iso as fresh install to upgrade from U7.10. My old set up was a dual boot system; 1 x 400GB SATA HDD (*"HDD1"* - Windows XP) + 1 x 40GB PATA HDD (*"HDD2"* - Ubuntu). Using grub, would boot neither O/S - worked just fine. Currently wanting to do the same thing but a number of issues with install:
 
U9.10 Installer would not detect *"HDD2" (see details of HDDS above) *but would detect *"HDD1"* and the presence of WinXP O/S. I trawled the forums and found a potential solution to this - ```
sudo apt-get remove dmraid
``` in terminal. Performing install again, both HDDS detected, **_but_** now fails to detect WinXP on *"HDD1"*. Urghh...
 
 

Well, I decided to continue with U9.10 install on *"HDD2"*. Funny thing is that it asks me if I want to migrate docos from WinXP (go figure). Anyway, manually allocating partitions:
[LIST]
[*]Primary partition (sda1) - 24GB, mount point "/", exf4
[*]Logical partition 1 - 4GB SWAP
[*]Logical partition 2 - 10GB FAT32, mount point /osshare
[/LIST]Continuing install, in the advanced tab selected /dev/sda1 as location for boot loader. Finished installation, set bios to boot *"HDD2"*, but does not boot GRUB (displayed is a blank screen that shows "Grub 2" at the top left had corner and nothing else.
 
I'm not sure why this has to be so difficult - no problems in the past doing this with U7.10. All I want to do is dual boot U9.10/WinXP using 2 different HDDS. Really, 2 issues here - failure to detect HDD / WinXP O/S + failure to successfully complete subsequent standalone install.
 
Can anyone shed light on the above issues.
 
Cheers
 
lhcpr

---

### Post by oldfred on 2010-02-21
Grub from the liveCd and if depending on which drive is first in BIOS may not install to the correct drive. This a particularly a problem in mixed SATA and PATA configuartions since the BIOS usually makes the PATA drive first. Older systems often ignored the BIOS but grub2 tries to follow the BIOS.

So we can see where thing got installed:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by lhcpr1 on 2010-02-22
Thanks - will give it a hit and get back to you next day or so

---

