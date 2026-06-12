---
title: "Dual boot WIN 8.1 &amp; UBUNTU trusty :- EUFI problem"
date: 2015-04-06
forum: Installation &amp; Upgrades
---

### Post by lashywants on 2015-04-06
Hi I have a new Toshiiba satelite L50D 136 english. I have read carefully and installed Ubuntu as recommended. However I am unable to choose op system with EUFI boot. If I choose Ubuntu  system says windows wont load . If i go into Eufi and choose CMS mode Ubuntu will open. I have tried to running  boot repair but it always says op aborted as i am in legacy mode

[https://paste.ubuntu.com/10750840/](https://paste.ubuntu.com/10750840/)

Windows black screen :-
 
file: /ubuntu/winboot/wubi7dr.mbr    status:0x000007b

My question is how do i get Ubuntu to run from Eufi and not legacy ?

Any suggestions gratefully recieved

lashy

---

### Post by slickymaster on 2015-04-06
Hi lashywants, welcome to the forums.

I moved your thread to the **Installation & Upgrades** sub-forum, which is the proper venue for it.

---

### Post by oldfred on 2015-04-06
Your post mentions wubi. That is not supported anymore as it does not work on gpt partitioned drives which all new systems with Windows 8 are. 

See links in the link in my signature for lots of useful info.

Often issues are common to one brand across several models, so the issue these users had and solved may also apply.
 Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba shows BCD entry
[http://ubuntuforums.org/showthread.php?t=2259331](http://ubuntuforums.org/showthread.php?t=2259331)
Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)
[SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Toshiba Satellite supergrub to boot to fix things
[http://ubuntuforums.org/showthread.php?t=2240884](http://ubuntuforums.org/showthread.php?t=2240884)
Toshiba C55D-A5163 - Installation of Lubuntu on computer with Windows 8.1 Feb 2015
[http://ubuntuforums.org/showthread.php?t=2267268](http://ubuntuforums.org/showthread.php?t=2267268)

---

### Post by hakuna_matata on 2015-04-06
> **lashywants said:**
> 
file: /ubuntu/winboot/wubi7dr.mbr    status:0x000007b

This means that wubildr.mbr doesn't work in UEFI mode. wubildr.mbr is part of a Wubi install but it is _not_ your current install. There is a second install without Wubi, too:
> 
[https://paste.ubuntu.com/10750840/](https://paste.ubuntu.com/10750840/)
```
/dev/sda6        /                        ext4       (rw)
/dev/sda7        /home                    ext4       (rw)
```
Unfortunately, Ubuntu is installed in legacy BIOS mode and Windows in UEFI mode. This is not a good idea.

IMHO an easy way would be to reinstall Ubuntu in UEFI mode. You have a separate /home partition and there is no need to overwrite it during install. But it is always a good idea to back up important data. It is always possible that something goes wrong.

---

### Post by lashywants on 2015-04-06
I am pretty much a newbi . how do i then reinstall in UEFI ???

---

### Post by oldfred on 2015-04-06
You have to boot installer in UEFI mode. How you boot is how it installs. But do not use anything automatic, just Something Else. Otherwise you may erase drive. And have good backups. See link below in my signature for warning.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

