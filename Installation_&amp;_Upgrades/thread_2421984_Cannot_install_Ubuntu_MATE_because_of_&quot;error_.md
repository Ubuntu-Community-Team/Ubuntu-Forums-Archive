---
title: "Cannot install Ubuntu MATE because of &quot;error: file '/boot/' not found.&quot;"
date: 2019-06-30
forum: Installation &amp; Upgrades
---

### Post by riccardoperraa on 2019-06-30
I created the live USB installation media with balenaEtcher using a downloaded Ubuntu MATE ISO (ver. 18.04.2 64-bit). Right before the grub appears, i get the error "error: file '/boot/' not found." and when I select the "Try Ubuntu MATE without installing" option, it just shows a black screen.

---

### Post by ubfan1 on 2019-06-30
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
   If using USB install media, use a  tool like unetbootin or rufus. 
   Don't just copy files to the USB.  
   See [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)  
3) Did you select the media check before trying to install?  
   See [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (perhaps another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media or
hardware problems.

---

