---
title: "installing from usb, ubuntu 13.10"
date: 2014-02-18
forum: Installation &amp; Upgrades
---

### Post by tom57 on 2014-02-18
I'm tying to boot from USB with Ubuntu 13.10 


I made it bootable with pendrivelinux.com's free tool. I also went into the BIOS and enable IOMMU Controller


Hardware Specs:
GIGABYTE GA-990FXA-UD3 AM3 Motherboard
AMD Semphron 145 processor
DDR3 4GB RAM


I get to right before I would put in my time zone information in the ubuntu install and nothings happens. The usb is made correctly with a 64bit Linux Ubuntu 13.10 image and seems to load from my old pc desktop, which i tested to make sure its good. But having difficulties to get past the Ubuntu load screen (see vid) with my new hardware. 



I have a video here that shows when it fails: [http://youtu.be/G3jolD-DphI](http://youtu.be/G3jolD-DphI)


thanks!

---

### Post by varunendra on 2014-02-18
Welcome to the forums tom57!

Your video shows it failing even before reaching the desktop, which is way before you would reach the time-zone selection screen.

What happens if you select the top option (Try without installing)? Do you get a working desktop? If yes, try installing from there. If not, the first thing to try would be the last option - "Test disc for defects".

If that is finished without errors, try manually adding "nomodeset" option to your boot line, as explained in the first post here : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

From your uploaded video, it does seem to be a graphics driver issue in which the 'nomodeset' option should help to give you at least a working desktop.

---

### Post by tom57 on 2014-02-18
You did see the Ubuntu Icon load for a few mins, correct? Thank you so much for helping :)

I cannot get through to a working desktop, i just scanned it found 2 errors found, says to press any key to reboot, but nothing seems to happen, ubuntu icon still appears to be loading something (although i think its stalled out)

i wonder if making the usb bootable on my 32bit windows XP caused any problems. I'm trying to make another bootable on my 64bit windows 7 right now to check.

not sure how to troubleshoot the 2 errors it found

---

### Post by varunendra on 2014-02-18
Did it also tell you which files were missing/corrupt?

And to check if the source ISO itself is intact : [**HowToMD5Sum**]("https://help.ubuntu.com/community/HowToMD5SUM")

If the generated MD5sum of the ISO doesn't match with its original MD5sum, then the ISO image itself is corrupt and you must re-download it.

If you happen to download the ISO again, I highly recommend downloading via torrents. It is not only faster, but ensures the integrity of the downloaded data too, since hash checking is a part of torrent protocols.

Link to official torrents : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

---

### Post by tom57 on 2014-02-18
thanks, im checking out your suggestions! it did not tell what files were corrupt, it seemed to stall out and not reboot when i pressed any key like it suggested.

in progress:
-got it to boot into Ubuntu without installing after creating a bootable usb again (on my 64bit windows 7)
-distortion going on when i open windows, although the taskbar is displayed correctly. 
- i have a button on videocard that changes the bios, and i've tried both with button off and on with same results (distored screen)
-after checking for defects: 2 files found and it won't let me progress by pressing any key to restart or show me names or files/errors
-currently, downloading torrent from suggested site and trying to boot from usb again. thinking either its a video card/image problem.

---

### Post by tom57 on 2014-02-18
its a video card issue for sure, i was able to get it loaded just using one video card instead of two. 

thank you so much for helping

---

### Post by fdrake on 2014-02-18
see if this work for you:

highlight "try ubntu" and press "e" and add this line to the console
replace "quiet splash” with “nomodeset" then press enter

---

