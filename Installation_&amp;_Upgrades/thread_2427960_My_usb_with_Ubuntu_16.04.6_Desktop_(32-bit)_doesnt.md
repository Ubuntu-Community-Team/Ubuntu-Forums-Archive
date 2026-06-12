---
title: "My usb with Ubuntu 16.04.6 Desktop (32-bit) doesnt boots from usb"
date: 2019-09-27
forum: Installation &amp; Upgrades
---

### Post by darkshadowhacker on 2019-09-27
Im trying to boot from usb ubuntu 16.04.6 to fix my GRUB with **Boot-Repair** because it says Error:Unknown filesystem but when i try to boot from usb it comes back to the boot selectin place and doenst boots

---

### Post by ubfan1 on 2019-09-30
1) Does your system meets the minimum requirements for your selected edition?
  See [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements).
  Lack of enough memory can cause boot failure of the install media. Select a
  lower requirement edition like Lubuntu or Xubutnu if necessary.
2) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
3) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
  If using USB install media, use a  tool like unetbootin or rufus. 
  Don't just copy files to the USB.  
  See [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)  
4) Did you select the media check before trying to install?  
  See [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
5) Did you ever do a "memory check" (perhaps another live-media menu choice) on your PC?

Doing the above can save you a lot of time struggling with a bad install media or
hardware problems.

---

