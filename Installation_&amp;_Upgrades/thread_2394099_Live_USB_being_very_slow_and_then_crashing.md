---
title: "Live USB being very slow and then crashing"
date: 2018-06-12
forum: Installation &amp; Upgrades
---

### Post by borhak on 2018-06-12
Hi,

When I test Ubuntu on my computer, it boots with no problems into the live USB. However, when I am using the live USB, the effects are very slow, up until a point in which the USB that has Ubuntu is detected as a drive. At that point, I can only move the mouse, but no program works.

Any idea how to fix this? I am scared to start instaling Ubuntu if it might suddenly crash as the live USB.

I am using a laptop with a Nvidia MX150.

Many thanks!

---

### Post by Autodave on 2018-06-12
Let's start with some specs on the laptop or at least make and model.

---

### Post by borhak on 2018-06-12
Oh sure, sorry about that, I am new. Thanks for taking the time!

So, the laptop is an ASUS ZenBook Flip 14 UX461UN.
It has: 
- Intel® Core&#8482; i7-8550U Processor
- Windows 10 (I am intending to do it dual boot after)
- NVIDIA® GeForce ® MX150
- 16GB 2133MHz LPDDR3 onboard
- 512GB PCIe® 3.0 x4 SSD
- If I am missing anything important, here are the specs for this laptop from the ASUS site [https://www.asus.com/2-in-1-PCs/ASUS-ZenBook-Flip-14-UX461UN/Tech-Specs/](https://www.asus.com/2-in-1-PCs/ASUS-ZenBook-Flip-14-UX461UN/Tech-Specs/)


I also tried the live USB using nomodeset, but still crashed when the USB containing the live USB was detected.

One of the times I was trying navigating, after clicking on the time to open the calendar, it threw me this error:
[https://ibb.co/dxKNNy](https://ibb.co/dxKNNy)

Then I choose to install instead of "try" from Grub, and when I was in the process, I got this error:
[https://ibb.co/ngeNNy](https://ibb.co/ngeNNy)

I tried the install again from grub to see what happens, and this time it crashed sooner with the following error:
[https://ibb.co/bBaoed](https://ibb.co/bBaoed)

I also checked that the USB and iso image were fine by using the same drive on a diferent laptop, and it worked with no problems.

Many thanks!

---

### Post by ubfan1 on 2018-06-12
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
Doing the above can save you a lot of time struggling with a bad install media or hardware problems.

---

### Post by borhak on 2018-06-13
Hi ubfan1, thanks for taking the time


1)So the checksum, I just checked it they matched well.
2)For the liveUSB, I used Rufus... the liveUSB also works fine on a different laptop.
3)I tried the media check and the installation device passed the test.
4)Did a memory check using Windows Memory Diagnostic and got no memory issues.

I suspect it might be a problem with the drivers... what do you think?

---

### Post by sudodus on 2018-06-13
Which version of Ubuntu is it?

I think the computer hardware is quite new (the graphics chip/card or some other piece of hardware might not have a new enough driver). You may have better luck with the newest possible Ubuntu or Ubuntu community flavour iso file.

You can find the daily iso files of

- Bionic (released as 18.04 LTS, but there are daily iso files aiming for point releases)

- Cosmic (to be released in October as 18.10).

These dailly iso files have software that are around 6 weeks newer now (from when 18.04 LTS was released), and if you are lucky, there might be a driver that works. If the problem is the graphics driver, I think you will still need the boot option nomodeset.

Sse this link to the [QA iso testing tracker](http://iso.qa.ubuntu.com/)

---

### Post by borhak on 2018-06-13
Hi, Many thanks for you answer sudodus.

So, I tried Cosmic from the link you left, and it worked perfectly! I guess I have to wait until October, but at least we know it should work.

Thank you very much, all the best!

---

### Post by sudodus on 2018-06-13
You are welcome :-)

---

