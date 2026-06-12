---
title: "Can't install Linux from USB on Lenovo"
date: 2015-01-09
forum: Installation &amp; Upgrades
---

### Post by eli_fabrikant on 2015-01-09
Hi you all,

I probably miss something big, but I searched the forums here and elsewhere and didn't find an answer.

I'm trying to install Ubunto on my new Lenovo Z50-70 and I can't seem to find a way to force the computer to boot from the USB stick before it launches into windows.

I already went into the bios menu, Boot manager, I disabled the fast boot, made sure the USB boot is enabled, but it didn't work.

The thing is, under boot devices I don't see USB. I even tried to do it through the pre-installed windows 8 and it restarted but showed me a message saying

''system doesn't have any USB boot option. Please select other boot option in boot manager menu''

What should I do now ? How can I add a USB boot option ?


Thanks in advance for any help!

e

---

### Post by oldfred on 2015-01-09
UEFI or BIOS will not show a flash drive that is not bootable.

So is flash drive correctly configured?
How did you create it and did you verify that ISO was correct?

       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)


 Note issues with 14.10 and older versions.
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)
And these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by eli_fabrikant on 2015-01-11
Great, it worked! thanks a lot oldfred :)

I used 'Start up disc creator' to copy the iso file onto the USB stick and the BIOS recognised it immediately.

---

