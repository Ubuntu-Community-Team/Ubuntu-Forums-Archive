---
title: "Screen Flashing and Brightness Issues"
date: 2017-09-14
forum: Installation &amp; Upgrades
---

### Post by skyfl4m3 on 2017-09-14
Hello,


I have a Toshiba Satellite L50-C-14U laptop previously running on Windows 10.
I have tried multiple methods to install Ubuntu, such as from a USB drive, CD, wiping the drive first or during installation etc...
However with every attempt I get a flashing screen during installation or boot, which sometimes loads after a very long time and sometimes never does.
I managed to get it installed once, however the only way to boot into the OS was through the recovery mode, then continuing to normal boot. Once on the desktop I could not control brightness in any way.
The system said the graphics were "gallium 0.4 on llvmpipe", yet the laptop has integrated Intel graphics (i3 processor).


I have attached a video of the problem [here]("https://photos.app.goo.gl/DYWB6696UGKgaWAH3"). I appreciate the quality is not great but it looks very much like a strobe light in real life.


I have also tried about every solution I could find online, so any help would be much appreciated (I am also new to Ubuntu and Linux in general).

---

### Post by DAB4970 on 2017-09-15
Hello

I've seen the screen brightness issues on BIOS release notes for my AIO (LX835-3203). Can you run Ubuntu off of your installation media before actually installing and run the lshw?

Check the installed bios version on your pc by using:

```
sudo lshw > Desktop/filename.txt
```

I use the redirect option to view the information in a separate gedit window as read-only.  Update your bios as needed.  And I'll try to post a link to my solved issue with updating the bios on my machine.

[https://ubuntuforums.org/showthread.php?t=2371380](https://ubuntuforums.org/showthread.php?t=2371380)

---

### Post by skyfl4m3 on 2017-09-17
Thanks for the reply.

I have checked and I am already running the latest BIOS version for the laptop, and was able to boot into the OS from the USB stick using the nomodeset boot parameter.

Attached are the results of the lshw command; [https://pastebin.com/Td1u9JyR](https://pastebin.com/Td1u9JyR)

---

### Post by DAB4970 on 2017-09-23
I don't understand what "nomodeset" is.  I did see that according to your lshw output, the video is integrated into the motherboard.  How old is the laptop?  
I am kinda thinking that it may be hardware.  Maybe not the integrated graphics, but could be the screen.

---

### Post by skyfl4m3 on 2017-09-23
I'm not entirely sure on the age of the laptop as it was given to me by somebody else. It is now discontinued by the manufacturer, and the only date I can find online is July 2015 - not sure how accurate this is but seems in the right area.

'nomodeset' is a boot parameter recommended online to use, which has an effect on the loading of the graphics drivers (from my understanding).

---

