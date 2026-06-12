---
title: "aim: 1. dual boot win8.1/ubuntu 1404 on acer aspire v571p and 2. fix up SSD"
date: 2015-02-28
forum: Installation &amp; Upgrades
---

### Post by Hodor on 2015-02-28
Two problems, I hope 1 post is OK:
1. I want to install a dual boot win 8.1 / ubuntu 14.04 on an acer aspire v571p-33214G50Mass:
- found some helpful stuff at [http://ubuntuforums.org/showthread.php?t=2142786](http://ubuntuforums.org/showthread.php?t=2142786), but wondering:
- is there some more recent (8.1/14.04) info specific to my model? I have not worked with UEFI before, it looks like trouble.
2. I tried to migrate a win 7 / ubuntu 14.04 installation from HDD to SSD and it did not go well:
- short version: I have a new SSD that is now a bit of a mess and I'm hoping GParted will fix it.
- Longer version: I used clonezilla to restore an image of the HDD to the new SSD => windows unhappy (dirty disk etc) => atttempted a clean install of windows 7 =>
-  I tried to delete and reformat the ubuntu partition while in the the win7 original installation program: and it deleted the partition but could not reformat it! 
- I've put the old HDD back in - computer working fine but SSD has this dead space that windows couldn't reformat. I'm waiting on an enclosure for the SSD (so I can plug it in while ubuntu is running) with the plan of using GParted to reformat the SSD. Any advice?
Thanks very much for any help.

---

### Post by oldfred on 2015-03-01
I believe in new clean installs, especially with Ubuntu. Not sure with Windows anymore as my last Windows was XP, and I never had to reinstall it. 

Is your Windows 7 UEFI or BIOS? Windows is very particular with partition sizes both start on drive & size in sectors and UUID type internal data. Makes it much more difficult to move. It is not intended  to be moved due to license restrictions.
If you have Windows 7 DVD, you have to convert to flash drive and do some updates to make it a UEFI installer. Some versions may work as is.

I think a lot of this is now older, but Acer issues would be the same even for different models. Vendors seem to have same issues on many similar models.
Newer version of Ubuntu does work better with Ultrabooks and other UEFI issues than those installs with older versions of Ubuntu. Each new version adds improvements. 
Also good to make sure you have newest UEFI/BIOS from Acer.

 Acer S7 14.04 & Windows 8.1 RAID
[http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest](http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest)
Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
acer aspire s7 Dual SSD RAID - [SOLVED] Installed Ubuntu on Pre- UEFI Win 
[http://ubuntuforums.org/showthread.php?t=2240043](http://ubuntuforums.org/showthread.php?t=2240043)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Added new msata drive post #3
[http://ubuntuforums.org/showthread.php?t=2174844](http://ubuntuforums.org/showthread.php?t=2174844)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

---

