---
title: "Installation of Lubuntu on computer with Windows 8.1"
date: 2015-02-28
forum: Installation &amp; Upgrades
---

### Post by mattharris4 on 2015-02-28
Yesterday I finally installed Lubuntu on my seven month old Toshiba C55D-A5163 (yes, I know I likely voided my warranty on at least my Windows installation and hard drive, that is why I originally was going to wait a year but Linux works better than Win 8.1 IMO).  The install using the default grapical dual-boot installer went smoothly and both Lubuntu and Windows worked normally after the install.  I had already disabled FastBoot and set it to first attempt booting from a USB stick before installing as I first tried Lubuntu running off of my USB drive.  After installation I did run into two issues.  

The first issue was my sound did not work.  Lubuntu for some reason loads with the volume muted at the terminal.  To unmute the sound, use the instructions here:  [http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/) (I know the instructions are for Ubuntu but alsamixer is also used in Lubuntu).  Essentially you use the terminal to enter alsamixer, use tab to get your cursor where it says "00" then press "M".  Using tab do that again until you have unmuted Master, Headphone and Speaker.  Increase the volume in alsamixer with your up and down keys until you are at the top of the scale.  That took care of the issue for me but instructions to reinstall alsamixer are shown at the above link. 

The second issue was I did not have Flash Player.  To get it, install the Ubuntu Software Center using the included Lubuntu Software Center.  After installation of the Ubuntu Software Center, search for "Pepper Flash Player".  Next, select the Pepper Flash Player from the list and install it.  Then Flash should work for Firefox (even though the article I am going to link to claims it won't work on it) and Chromium.  Here is a link: [http://www.howtogeek.com/193876/using-firefox-on-linux-your-flash-player-is-old-and-outdated/](http://www.howtogeek.com/193876/using-firefox-on-linux-your-flash-player-is-old-and-outdated/) .  You could also install Chrome but I did and found that it only allowed Flash to work with Chrome and not Firefox and Chromium (I usually use Firefox so this solution would not do for me, I then did more searching and found the link in this paragraph).  Pepper Flash Player does not update nor notify you of updates so keep this link in your bookmarks and use the instructions provided to check for updates and then update monthly if needed.

I also used the info in this link to help me:  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

My Toshiba has an AMD E1-2100 processor running 1.0GHz, is 64 bit, a 500GB hard drive, 4GB of RAM and a 15 inch screen.  There is plenty of RAM even for Windows 8.1 but the processor is meant for power conservation and not performance and easily maxes out in general use.  With Lubuntu it maxes out less often and works more smoothly than with Win 8.1.

I am going to bookmark this thread and report if I find anything else.  Please post with your installation reports, they may help others in their installs.  Hopefully your installs go as smoothly or even more smoothly than mine.

---

