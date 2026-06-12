---
title: "Loading Ubuntu From usb"
date: 2014-12-31
forum: Installation &amp; Upgrades
---

### Post by milhouse2 on 2014-12-31
I am loading Ubuntu 14.04 from UNetbootin loaded on to a usb and when it tries to boot it goes to grub. I have loaded a few O/S's and never seen this they would just  load the os. Is there a command I need to type in to start? I am just headed to search this grub to see if I can figure it out from there but any help would be great. 
Thanks

says on the screen

                                           GNU GRUB version 2.02
something about command push with a few more things

GRUB:

---

### Post by ubfan1 on 2014-12-31
If you're at grub, you have successfully booted, whatever type (UEFI/BIOS) of machine you have. Lets start at the beginning:
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media.

---

### Post by milhouse2 on 2014-12-31
Thanks for this i will look threw thing  and see if i can get it to fire up 
Cheers

---

### Post by sudodus on 2014-12-31
Welcome to the Ubuntu Forums :-)

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It makes it easier to give good advice :-)

And see this link about booting from USB

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by milhouse2 on 2015-01-01
I tried a other usb loader and got it to load today  looks to be working good
thank you for the help

---

### Post by sudodus on 2015-01-01
Congratulations :KS

Please click on Thread Tools at the top of the page and mark this thread as SOLVED

---

