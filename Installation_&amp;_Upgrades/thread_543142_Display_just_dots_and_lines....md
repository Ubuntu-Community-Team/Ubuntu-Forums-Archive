---
title: "Display just dots and lines..."
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by weelubo on 2007-09-04
Hi,

I've just installed Ubuntu 7.04 using the text install however once the machine reboots i can hear the welcome sound but the display is just a mass of vertical lines. 
I tried again booting into the Live CD and the same thing happened, it appears that there are a number of users with similar display problems however most of these seem to be 'no display' issues rather than 'strange display' issues. I have read loads of posts on this but can't find a solution, many of the others were resolved by opening a terminal window and typing something but i literally can't see any objects only lines, even when i key CTRL-ALT-F1 so i am limited in what i can do/

I did manage to see the desktop when i used the Live CD in Safe Graphics Mode but this is obviously booting from the disc rather than the HDD and i don't know how to fix the OS on my HDD.

I'm running an Intel Core2Due e6600 with 4GB RAM and using an nVidia GeForce 7600 GT. I have dual display, the VGA output is the vertical lines and the HD output is a black screen with broken vertical lines and dots. No objects, windows or cursor...

Can anyone help....

Thanks in advance

---

### Post by steveneddy on 2007-09-04
Just a suggestion, but you might try unplugging one of the displays before you boot up and configure xorg.conf after you have installed xcinerama or something equivalent and then the appropriate video card drivers.

I think that the multiple monitor situation is too much for the default vesa video driver.

This is just my two cents.

Hope it works.

:popcorn:

---

### Post by weelubo on 2007-09-04
Thanks for the response. I tried without the HDMI but no luck, not sure what the other thing is you said to try. I haven't installed anything other than the OS. Not sure how to configure xorg or if its even possible given the display issues...
You can see what us happening here [http://img468.imageshack.us/img468/1470/displaynz5.png](http://img468.imageshack.us/img468/1470/displaynz5.png)

Thanks

---

### Post by Pumalite on 2007-09-04
[http://ubuntuforums.org/showthread.php?t=240150](http://ubuntuforums.org/showthread.php?t=240150)

[http://ubuntuforums.org/archive/index.php/t-239906.html](http://ubuntuforums.org/archive/index.php/t-239906.html)

---

### Post by Pumalite on 2007-09-04
I just got this from another thread; it might help you:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by weelubo on 2007-09-05
Hi,

Thanks for trying, unfortunately dual monitor display is not my problem, i am now using only the standard VGA monitor and still have no display. I cannot boot into CLI because i can't see anything...

Is there anyway to boot from the CD into the Safe Graphics Mode and from there install the video driver onto the OS stored on my HD?

Thanks again

---

### Post by weelubo on 2007-09-06
Anyone? I'm about to reinstate some NTFS storage space..... :(

---

### Post by Pumalite on 2007-09-06
I personally think that if you connected an RGB to your card, you would have no problems. I might be wrong; but, it's my guess.

---

### Post by weelubo on 2007-09-06
RGB? Is this VGA? There are only 2 sockets on the card DVI/VGA and HDMI, both give a similar result...

---

### Post by Pumalite on 2007-09-06
Just a regular 17 inch monitor. Then, once IN the system (if it works), you can connect your other monitors after downloading appropriate driver and adjusting your resolutions.

---

### Post by weelubo on 2007-09-08
The monitor is a Samsung SyncMaster 940n it is a standard VGA monitor, i also have the HDMI to my TV but i have removed this since the fault. 

Thanks

---

### Post by Pumalite on 2007-09-08
Is it working now?

---

### Post by weelubo on 2007-09-09
No

---

### Post by Pumalite on 2007-09-09
Sorry, but I ran out of ideas. Someone else will chime in.

---

