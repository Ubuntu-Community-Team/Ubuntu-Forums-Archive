---
title: "Install issues with Dell Inspiron 3520  -Dual boot"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by leeston on 2013-02-22
Hi,
 I have just purchased a Dell Inspiron 3520 with Window's 8 64 bit installed. I downloaded the  Windows .exe file to get the latest Ubuntu dual boot OS and after install, got the following screen :  
 

 Windows Boot Manager
 

 Windows failed to start. A recent hardware or software change might be the cause. Bla bla bla
 

 File: \ubuntu\winboot\wubildr.mbr
 

 Status : 0xc000007b
 

 I press enter, and the dual boot screen comes up – I select Ubuntu and it goes around in a loop back into the above screen.  
 

 I regret although an avid user of Ubuntu, I am not that familiar with the techy side so would appreciate an idiots guide, so to speak on how to over come this issue so that I can access to Ubuntu  via the dual boot screen  …......   
 

 Your help would be gratefully appreciated.

---

### Post by oldfred on 2013-02-22
Wubi does not work with gpt partitioned drives. 

Windows 8 with UEFI only works with gpt drives. so you cannot install with wubi.

But with gpt drives you can easily create as many partitions as you want, but Windows 8 has UEFI which is new and then has added the secure boot feature (?) which may complicate the install. 

Some new systems also have issues with Intel SRT or video drivers. Is this an UltraBook or dual video?

Dell's do seem to be ones that work with dual booting and UEFI.

       Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
         HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache) - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
    
    Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

---

### Post by Sgnob on 2013-03-02
I have the same laptop with windows 8 pre installed.. I could not get 12.10 64 bit to even run from disk with secure boot on. Try going into BIOS and turn secure boot off.. Worked for me. Graphics are a little buggy (core i3 using sandy bridge) and my wifi didnt work at first but found the fix here in another one of my posts. 

[http://ubuntuforums.org/showthread.php?t=2087941](http://ubuntuforums.org/showthread.php?t=2087941)

Also I manualy partition my drive in windows 8 and installed ubuntu on the new partition. I was not able to get wubi or grub to work right with windos 8. no problem for me as I mainly use ubuntu and only needed to use windows once since i'v had this lap top.. I have the ubuntu partition selected to boot first in my boot order and when windos is needed simply press f12 when booting up and select the windows partition. With out grub installed my computer boots up in like 30 seconds or less which I really like. It takes my desk top at least 60 seconds or more just to boot up grub. 

Hope this help and please post your results as I'm still learning linux.
Sgnob

---

