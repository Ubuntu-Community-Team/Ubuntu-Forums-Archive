---
title: "[SOLVED] Installation not working:  Video Woes"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by kgriff on 2008-04-19
I am trying to install 7.10 on a new system with the following components:
Mobo:  Gigabyte GA-MA770-S3
Processor:  AMD Athlon 64 X2 5200+
RAM:  2GB Kingston
Video: Asus EN8400GS (Nvidia)
HDD:  80GB SATA

When I initially boot from the CD, I get to the initial Ubuntu boot selection screen.  If I select Start in Safe Graphics Mode, my screen goes blank with only a blinking cursor in the upper left corner.  The only way I can get any result other than this is to select VGA mode 1024x768x32.
The second graphic screen, with the Ubuntu logo and progress bar is displayed okay for a while, then kinda goes haywire.  The progress bar turns into 3 progress bars staggered left to right and top to bottom, across the center half of the screen.  The top bar is half width and is stationary with no activity.  The center bar is normal size and shows the moving progress indicator.  The bottom bar is quarter size and is also stationary with no activity.

Eventually, I get a message box, "Ubuntu is running low graphics mode.  Your screen and graphics card could not be detected correctly..."  If I select continue to proceed in low-graphics mode, I again get a black screen with only a cursor in the upper left corner.  If I select Configure, I can manually configure my display.  Selection of the generic VGA driver, and any video resolution, again results in a black screen when I do the video "Test".  If I select the vesa driver, I can run the video test, but no resolution that is supported by my monitor gives a correct display.  

I'm currently downloading 8.04 in hopes that this will help things to work better.  However, any suggestions that may help me get 7.10 installed, or 8.04 once I have the iso burned, would be greatly appreciated.  (Would Kubuntu work any differently, since it is using KDE rather than Gnome?  Please excuse me if this sounds like an ignorant question, but until a few weeks ago, my only experience with Linux was Red Hat 8 or 9 years ago.  As far as I'm concerned, I'm a raw beginner.)

---

### Post by Partyboi2 on 2008-04-19
You could try using the [alternate cd]("http://releases.ubuntu.com/7.10/") to install which is a text base installer.

---

### Post by kgriff on 2008-04-19
Where can I find some guidance for installation from the alternate CD?  I'm assuming this is more of a command line driven install?  Last time I did a Linux command line install was Red Hat, years ago.

---

### Post by Partyboi2 on 2008-04-19
[This]("http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2") stream will show you how to install using the alternate cd. It is pretty easy to install. If you are wanting screenshots you can look [here]("http://news.softpedia.com/news/Encrypted-Ubuntu-7-10-68383.shtml"). (you can skip the section of encrypting if you want)[COLOR=#6C7AA1][/COLOR]

---

### Post by kgriff on 2008-04-21
Thanks for your help.  The alternate install was a snap.  Video still not right, but that is a problem for a different post.

---

