---
title: "Ubuntu 12.10 can't get 1920x1200"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by Orange Kingdom on 2012-11-25
Hi,

I just installed Ubuntu 12.10 and it boots in '1995' 1024x768 mode.
In display settings there is only 1024 and no 1920x1200  option.
I have a Nvidia GT220 card.
I don't want to poke in xorg files.
I am using the default Nouveau driver (is it real nouveau?) and i tried the Nvidia driver in the software center with no luck.
How can i change the resolution?
Please say it is possible (easy).

thank you.

---

### Post by cariboo on 2012-11-25
> **Orange Kingdom said:**
> Hi,

I just installed Ubuntu 12.10 and it boots in '1995' 1024x768 mode.
In display settings there is only 1024 and no 1920x1200  option.
I have a Nvidia GT220 card.
I don't want to poke in xorg files.
I am using the default Nouveau driver (is it real nouveau?) and i tried the Nvidia driver in the software center with no luck.
How can i change the resolution?
Please say it is possible (easy).

thank you.

I have a GeForce 210 [noparse](GT218)[/noparse], for me the only driver that worked in Quantal is nvidia-current-updates. Once you've got that installed, press the Super key and type nv, then run Nvidia Xserver Settings to set your resolution.

---

### Post by oldfred on 2012-11-25
With 12.10 I had to install the kernel headers first, then nVidia correctly installed. Example below is with nvidia-current and settings, but I also installed the nvidia-current-updates and settings updates. Versions must be consistent.

       [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
    
       # You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot

    
       May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*


       
 Fix for nVidia with 12.10 missing kernel dpkg reconfigure:
[http://ubuntuforums.org/showthread.php?t=2072862](http://ubuntuforums.org/showthread.php?t=2072862)

---

### Post by jm719 on 2013-01-07
I would love for someone to get on Nvidia's case about not supporting 1920x1200 on multiple (e.g. second) monitors. I have gone back and forth with one of Nvidia's engineers, who, in the end, just said their newest video cards and drivers did not have multi-monitor support for 1920x1200. He said he would look into fixing it, but does not answer any of my posts to the case number of my problem report.  I have two different 1920x1200 monitors. Both monitors work fine on an old Dell M90 with an FX2500M. Both also work fine on an older desktop. I have an newer Alienware with a pair of GTX460M but it does not drive the 1920x1200 monitors properly.  The Nvidia control panel recognizes the 1920x1200, but overscans the monitors. I have to set the Nvidia control panel to "scale" the size down so that I can see everything that I'm supposed to see (i.e. to all the screen edges). I also have a newer desktop with a pair of GTX570. Again, neither monitor works. I know the monitors are fine because they work with older Nvidia cards. The scaling is lousy and causes letters to have a morey pattern that gets lighter and darkers as you drag a window around on the screen. Poor poor, poor, yet Nvidia has not fixed it for several years now! I always do a complete fresh install with each new rev of their drivers, but to no avail. I'm on  It's still busted. I'm using rev 310.90.  If anyone has some fix for this, I am all ears. Thanks!
John

---

