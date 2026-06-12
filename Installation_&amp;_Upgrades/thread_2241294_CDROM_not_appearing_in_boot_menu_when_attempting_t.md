---
title: "CDROM not appearing in boot menu when attempting to install Ubuntu 14.04 from a disk."
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by PlagueGiver on 2014-08-25
I recently purchase a Linux Format magazine entitled "ESCAPE WINDOWS". When I turned to the page in which was described the process during which I would back up my files using SystemRescueCD and attempted to follow the instructions, I encountered a problem on the very first stage. I placed the CD in my CD DRIVE and restarted my laptop, then pressed F12 to enter the Boot Menu. At this point, the CD ROM was not in the menu. I was forced to exit and watch the laptop switch on. I have tried this repeatedly, and encountered the same results. I am not in possession of a hard drive, so it will be extremely difficult for me to use the Windows SystemImageBackup utility.

---

### Post by grahammechanical on 2014-08-25
You may need to change some setting in the boot system (BIOS/UEFI) to allow the boot system to look to the CD/DVD drive as a possible source of an operating system.

---

### Post by PlagueGiver on 2014-08-25
Do you have any idea how? I am using a Toshiba laptop, satellite p755-s5380, and am running Windows 7. I am quite new to this kind of thing, and I don't want to break anything.

Thanks.

---

### Post by grahammechanical on 2014-08-25
> [COLOR=#000000]and I don't want to break anything.[/COLOR]

And without any experience of that machine any advice given here would irresponsible because if we get it wrong something is sure to be broken. You need to find instructions from the manufacturer on doing this. Is there not a hand book? Or a user guide?

---

### Post by slickymaster on 2014-08-25
You can get the manual for your model here: [http://support.toshiba.com/support/staticContentDetail?contentId=3115991&isFromTOCLink=false](http://support.toshiba.com/support/staticContentDetail?contentId=3115991&isFromTOCLink=false)

---

### Post by PlagueGiver on 2014-08-25
Do you have a download link for that? It's extremely difficult to locate the part about the boot menu, since the CTRL+F function does not seem to work on that particular page.

---

### Post by PlagueGiver on 2014-08-25
If this is too complicated, does anybody know if it's possible to move the contents of the CD onto a USB or Hard Drive and boot it from that? If so, please share details.

---

### Post by slickymaster on 2014-08-26
> **PlagueGiver said:**
> Do you have a download link for that? It's extremely difficult to locate the part about the boot menu, since the CTRL+F function does not seem to work on that particular page.

The link I provided you will open the manual as a PDF in your browser and thus you're able to save a copy of it in your computer.

Anyway, what you're looking for is in page 164-165, under the TOSHIBA Hardware Setup sub-chapter:
> TOSHIBA Hardware Setup is the TOSHIBA configuration management tool available through the Windows® operating system. To access it: Click Start -> All Programs -> TOSHIBA -> Utilities, and then HWSetup, or click the TOSHIBA Hardware Settings icon in the Optimize tab of TOSHIBA Assist.
The TOSHIBA HWSetup screen have the following tabs:
[LIST]
[*]Boot Setting—Allows you to change the sequence in which your computer searches the drives for the operating system. You can also manually choose the Boot Setting by pressing the power button to power on the computer, then quickly pressing the F12 key. Select the boot device by pressing the arrow keys, then pressing the Enter key.
[/LIST]


---

### Post by yancek on 2014-08-26
If you have problems with the CD, you can put most Linux systems on a flash drive.  Just google unetbootin (separate versions for Linux windows, get the windows) or pendrivelinux which needs to be run from windows.  Simple instructions are on their home page and if don properly, you will be able to boot from them.

---

### Post by PlagueGiver on 2014-08-26
Since I am unable to currently download the unetbootin, could I simply copy the contents of the cd onto a USB and have it work the same way? 

Thanks!

---

### Post by PlagueGiver on 2014-08-28
bump

---

### Post by yancek on 2014-08-28
> Since I am unable to currently download the unetbootin, could I simply  copy the contents of the cd onto a USB and have it work the same way? 

No.  Well, it's technically possible but way to complicated.  It seems your problem is simply that you are unable to change the boot priority in the BIOS which according to posts above, should be accessible immediately after booting by repeatedly tapping the F12 key.  When you initially boot, do you see a screen with a Toshiba logo, at the bottom of that screen it should tell you a key to presse to "enter setup", do you see anything there.

---

### Post by PlagueGiver on 2014-09-01
Writing from linux! Thread is definitely SOLVED! Thanks guys! I just had to press C when booting

---

