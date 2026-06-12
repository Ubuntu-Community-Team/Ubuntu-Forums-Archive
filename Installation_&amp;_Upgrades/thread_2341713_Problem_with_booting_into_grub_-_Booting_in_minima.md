---
title: "Problem with booting into grub - Booting in minimal bash instead"
date: 2016-10-30
forum: Installation &amp; Upgrades
---

### Post by Delta_Unit_117 on 2016-10-30
I have a problem with my laptop (A HP Stream 11 (2015 version)). It isn't not booting into Ubuntu properly after I've installed it.
The installation is on a SD card since I have no space left on my main drive. 
Basically when I wanted to boot into Ubuntu, it gets into minimal bash of GRUB. I reinstalled it several times but still get the same results.

I am running in EFI mode with secure boot on, just to be sure. Though I disabled secure boot before just to check if that would've fixed it, but of course it didn't.

Any idea how to solve this problem or should I try to install it on my main drive instead?

---

### Post by oldfred on 2016-10-31
While it should work with Secure boot on, may be better to try with it off.
Grub menu will not boot Windows if Secure boot is on, but you can boot from UEFI menu.

Make sure you have newest UEFI/BIOS from HP.

HP has not been UEFI boot friendly. It violated UEFI standard that specifically says not to use description as part of boot. And only valid description is "Windows Boot Manager". But there are multiple work arounds. If dual booting many copy shimx64.efi to /EFI/Boot/bootx64.efi which is a fallback or hard drive boot. If you run Boot-Repair with this checked 'Use the standard EFI file' in advanced options.     
Then you should be able to boot the hard drive entry in HP, some may have to add that entry.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

HP has similar UEFI with most models:

 Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
Envy M6 Change boot order sudo efibootmgr -o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

---

