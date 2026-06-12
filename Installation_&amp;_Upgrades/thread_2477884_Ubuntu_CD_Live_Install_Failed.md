---
title: "Ubuntu CD Live Install Failed"
date: 2022-08-09
forum: Installation &amp; Upgrades
---

### Post by mjberey on 2022-08-09
Have MX on one computer and Mint on another. Trying to install Kubuntu 22.04 on either of them from DVD drive attached to USB. Message on both computers is the following:

"Failed to Start Ubuntu CD Live Install Failed"

Any suggestions would be appreciated

---

### Post by ubfan1 on 2022-08-10
1) Does your system meets the minimum requirements for your selected edition?
  See [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
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

