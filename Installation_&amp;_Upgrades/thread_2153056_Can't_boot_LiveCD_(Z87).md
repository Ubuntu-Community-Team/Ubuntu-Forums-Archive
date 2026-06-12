---
title: "Can't boot LiveCD (Z87)"
date: 2013-06-10
forum: Installation &amp; Upgrades
---

### Post by wujj123456 on 2013-06-10
Update: The problem is really GTX 780.  Everything works fine on Intel HD4600.

Has anyone using the latest Haswell platform booted the LiveCD successfully?  I've tried Ubuntu and Ubuntu Gnome.  They are written to my USB stick using the universal USB installer.  I can see the boot menu, but when I select Try Ubuntu, the screen just goes black.  I don't think it's reading the stick either, but I still waited for quite a few minutes.  

I've installed Ubuntu several times since 8.04, and this is the first time I had such an issue.  Is it because Ubuntu 13.04 came earlier than Z87, so the platform is not well tested?  Has anyone successfully installed Ubuntu on Z87?

PS: I've already disabled those Windows 8 crap in UEFI (like quick boot, secure boot).  My Windows 8 is installed in UEFI mode, and I believe I need to go through the UEFI hassle when installing Ubuntu as well.  But I want to at least get into the LiveCD first just to make sure everything could work...

---

### Post by fantab on 2013-06-10
Screen going 'black' could mean that it is a video/graphics issue. What Graphics do you have there?
Have you tried the '[**NOMODESET**]("http://ubuntuforums.org/showthread.php?t=1613132")' option?

---

### Post by oldfred on 2013-06-10
It will work, but this site updates to the very newest kernel and video for its tests. Not sure then what settings are used.
[http://www.phoronix.com/scan.php?page=article&item=intel_haswell_2d&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_haswell_2d&num=1)

---

### Post by wujj123456 on 2013-06-11
Thank you so much.  You guys are excellent.

It's indeed my GTX 780.  I first removed my GTX 780 and was able to boot the LiveCD and finish installation off HD4600.  If I plug it back in, the black screen comes back.  If I do nomodeset, I can get past the black screen.  However, due to GNOME's requirement of HW-accelarated graphics I guess, I am forever stuck at login screen.  Even Ctrl+Alt+F1 won't bring up a terminal.  I was able to drop down in to recovery mode though.

Now I understand why Linus gave Nvidia a mid finger...  Yeah, the proprietary driver might be better than AMD's, but there are times I don't even have a chance to use it.  I guess if Intel didn't have integrated graphs, I am pretty much screwed.

Nvidia-current driver won't work.  Manual nvidia installation didn't work either.  Looks like I need to advance to mainline kernel and use nvidia-current from xorgs ppa.  I will continue tomorrow.

---

### Post by wujj123456 on 2013-06-12
OK. I give up.  After trying numerals combinations of xorg/kernel/driver, it still won't boot with GTX 780 in the slot.  So my question is: is there a way to force Linux to ignore the Nvidia cards?  I am quite OK with the performance of HD4600 for my Linux Desktop, but I don't want to open my case just to switch OS.

---

### Post by oldfred on 2013-06-12
Not sure but if you uninstall all the nVidia drivers and make sure your are using the Intel driver would that not work?
I have not manually configured an xorg for eons, but someone may have a suggestion.

       # Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

 Intel xorg file:
[http://ubuntuforums.org/showthread.php?t=1484137](http://ubuntuforums.org/showthread.php?t=1484137)

Total uninstall and reinstall X11 video
[http://lkubuntu.wordpress.com/2011/08/30/quick-and-easy-way-to-fix-x11-issues/](http://lkubuntu.wordpress.com/2011/08/30/quick-and-easy-way-to-fix-x11-issues/)

---

### Post by wujj123456 on 2013-06-12
> **oldfred said:**
> Not sure but if you uninstall all the nVidia drivers and make sure your are using the Intel driver would that not work?
I have not manually configured an xorg for eons, but someone may have a suggestion.

       # Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

 Intel xorg file:
[http://ubuntuforums.org/showthread.php?t=1484137](http://ubuntuforums.org/showthread.php?t=1484137)

Total uninstall and reinstall X11 video
[http://lkubuntu.wordpress.com/2011/08/30/quick-and-easy-way-to-fix-x11-issues/](http://lkubuntu.wordpress.com/2011/08/30/quick-and-easy-way-to-fix-x11-issues/)

I've tried that first actually. Without installing any nvidia drivers, I plugged in the 780. As long as the display is connected to 780, hdmi port on the motherboard is disabled.

I guess there is probably no way to just using HD4600 with discrete graphics connected, unless it's a Optimus enabled laptop...

---

