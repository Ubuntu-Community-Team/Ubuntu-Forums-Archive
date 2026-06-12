---
title: "[Help] nouveau fifo error trying to install ubuntu 16.04 lts"
date: 2018-01-15
forum: Installation &amp; Upgrades
---

### Post by mangoknife on 2018-01-15
Hey 
Im trying to install linux ubuntu next to my windows 10 but whenever i boot from usb after a few seconda i get 
Alot of this errors;
... [06.432831] nouveau 0000:65:00.0: fifo: SCHED_ERROR 08 [] ...

I have gtx 1080 ti with i7 7700k
I tried this method [https://ubuntuforums.org/showthread.php?t=1613132&page=11](https://ubuntuforums.org/showthread.php?t=1613132&page=11)
But i dont have any purple screen to begin with and the pictures are broken
Help?

---

### Post by ubfan1 on 2018-01-15
On the black grub screen (UEFI boot), move to the Ubuntu selection if not first, and type e to edit (instructions at bottom of screen).  Move the cursor to the line starting with "linux", and at the end, add the word nomodeset (usually at the words "splash quiet").  That should let you boot, login, update your packages, and then try the Software and Updates/ Additional Drivers tab to add the proprietary Nvidia drivers.

---

### Post by mangoknife on 2018-01-16
> **ubfan1 said:**
> On the black grub screen (UEFI boot), move to the Ubuntu selection if not first, and type e to edit (instructions at bottom of screen).  Move the cursor to the line starting with "linux", and at the end, add the word nomodeset (usually at the words "splash quiet").  That should let you boot, login, update your packages, and then try the Software and Updates/ Additional Drivers tab to add the proprietary Nvidia drivers.

Thanks ill try it

---

### Post by mangoknife on 2018-01-16
> **ubfan1 said:**
> On the black grub screen (UEFI boot), move to the Ubuntu selection if not first, and type e to edit (instructions at bottom of screen).  Move the cursor to the line starting with "linux", and at the end, add the word nomodeset (usually at the words "splash quiet").  That should let you boot, login, update your packages, and then try the Software and Updates/ Additional Drivers tab to add the proprietary Nvidia drivers.
Hey
I pressed edit (its tab not e btw)
I had 'quiet splash ---'
I deleted the "---" and typed nomodeset and pressed enter
It took me to the install loading screen than after a second it send me to this screen:
[https://streamable.com/bjbqa](https://streamable.com/bjbqa)
What should i do from here?

---

### Post by ubfan1 on 2018-01-16
Maybe the "---" should have been left last, after the nomodeset. 
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

### Post by mangoknife on 2018-01-16
> **ubfan1 said:**
> Maybe the "---" should have been left last, after the nomodeset. 
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

Thanks for your help
I was able to solve the problem
None of thw things you sugvested worked sadly so i tried to maybe install 17.10.1
And it worked!
17.10.1 apparently support gtx 1080 ti i guess
So yeah it worked out
I think we should let people know about this so they wont get into trouble like i did
Thanks for all thw help btw :)

---

