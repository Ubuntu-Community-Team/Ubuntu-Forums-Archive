---
title: "problem installing lubuntu 18/19"
date: 2019-07-23
forum: Installation &amp; Upgrades
---

### Post by sxnii13 on 2019-07-23
Hello, first of all excuse my English, I do not speak English and use the translator.  I have decided to install a 3.06GHz celeron with 2 GB of ram on my pc.  I try to install it from a usb since the dvd readers of my pc do not work correctly, everything goes well until it is time to install the system, that the installer window goes black and does nothing anymore, does usb reading  about 2-3 minutes and does nothing again.  What solution do you have?  P.D: I have done the bootable USB with rufus using the 64 bit iso, since my processor supports 64 bit

---

### Post by ubfan1 on 2019-07-24
1) Did you hashcheck check the downloaded iso?
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

Doing the above can save you a lot of time struggling with a bad install media or hardware problems.

---

### Post by Rubi1200 on 2019-07-24
Just to add to the good advice from ubfan1 above, if your system has lower specifications you might want to consider something lighter like Lubuntu or Xubuntu instead.

And best to always choose LTS versions; they are more stable and have longer support.

---

