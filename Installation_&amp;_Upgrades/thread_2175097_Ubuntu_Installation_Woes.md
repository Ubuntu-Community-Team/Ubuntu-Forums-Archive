---
title: "Ubuntu Installation Woes"
date: 2013-09-17
forum: Installation &amp; Upgrades
---

### Post by brutikk on 2013-09-17
I have a new laptop, an Asus atheros/ar5b225, and have not been successful in installing Ubuntu.  The laptop is running Windows 8, and is 64bit.

My first attempt was to install Ubuntu 13.04 by downloading the iso, putting it on a thumb drive (via unetbootin), booting to the USB, and installing.  This brought me to the screen "Try" or "Install" Ubuntu.  Clicking either option results in the USB's light turning off (maybe it stopped being recognized somehow?), and the screen remaining blank for at least 10 minutes (I stopped waiting after then).  I decided to redownload the .iso and put it on the thumb drive again, in case of a corrupt download somehow.  I had the same results.

So, I decided to settle for 12.04.  I used the windows installer and allotted Ubuntu 30GB of space.  Everything went fine, and there were no errors.  After rebooting, I received an error message stating that "Windows could not start" (despite trying to boot in to ubuntu), and:

```
File: \ubuntu\winboot\wubildr.mbr
State: 0xc000007b
```


I am also brought to the Windows boot manager screen now, which will only let me boot in to Windows 8.

Here is what I would like:

: Ubuntu 13.04 to be installed alongside Windows 8 (I would settle for just this)
: Not to use the Windows 8 boot manager (Optional, but preferred)

Any assistance in this matter would be greatly appreciated.

---

### Post by mastablasta on 2013-09-18
i don't think wubi will work in this case.

more on UEFI and new mashcines: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by brutikk on 2013-09-19
How would I get rid of the damage done by the wubi installer?  I.e., how would I remove the installation?

---

### Post by mastablasta on 2013-09-19
if you can boot into windows uninstall wubi/ubuntu in control panel (? it used to be control panel add/remove programmes i don't know how it is in windows 8). it installed like a programe, so it will also uninstall like one (hopefully).

if not, you can probably delete it and repair windows MBR: [http://www.redmondpie.com/how-to-fix-windows-8-mbr-master-boot-record/](http://www.redmondpie.com/how-to-fix-windows-8-mbr-master-boot-record/)

---

### Post by oldfred on 2013-09-19
Other Asus threads, not sure how similar to yours. One model K55N has not been posted to work with UEFI.

  Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Asus UltraBook - kernel comparisons K56CA
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)
Asus Zenbook Prime UX31A (UEFI)  Blank screen resolved by turning secure boot off, many tests of Boot parameters
[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)
 install 13.04 on asus ux32a, problems with usb boot - several reports working well no details
[http://ubuntuforums.org/showthread.php?t=2146440](http://ubuntuforums.org/showthread.php?t=2146440)

---

