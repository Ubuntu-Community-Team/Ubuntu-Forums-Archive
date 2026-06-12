---
title: "Windows dynamic disk error in 8.04"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by aces170 on 2008-05-24
I tried installing using a USB pen drive using 
[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

I lost my data on the hdd, was not able to partition kept getting the error parted cannot partition a disk using windows dynamic disk, I got the error in the guided as well as manual partioning process

My optical drive has got spoilt hence cannot use a CD or a DVD...

---

### Post by Pumalite on 2008-05-24
Maybe this would help:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by aces170 on 2008-05-25
Ok, I have managed to intsall 8.04 finally, was able to get the net started without hiccups.

The prob is I cannot access my main windows disk, it says "invalid mount option while attempting to mount the device" I can post the screenshot if required

---

### Post by aces170 on 2008-05-25
Have some other issues too:

Now the issue, is getting decent performance in divx and xvid videos, the image quality on the default totem player is horrible. The video is also very choppy (I have an onboard 690G system) the ATI drivers are enabled, surprisingly in the add/remove repositories it shows KMplayer (KDE version of Mplayer) and I am pretty confident that I have the GNOME desktop environment.

I have downloaded the .tar version of Mplayer but have no clue on how to install it...

BTW what is windows dynamic disk management ?

Some help will be grateful...

---

### Post by Pumalite on 2008-05-25
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)
ATI does not support Linux. You might want to try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by aces170 on 2008-05-25
^^ Hey thanks for the tutorial link is really helpful, am able to install Mplayer but it yet cant play video files.

I was getting 
"Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"
when I tried to use the 2nd command

Also are you sure ATI/AMD does not support Linux because they do have Linux drivers, should I install them or the ones installed by hardy by defualt good enough ? Video is never so choppy in windows.. Now only if I can get the video working can get a breather from the virus infected Windows XP :)

---

### Post by Pumalite on 2008-05-25
Make Medibuntu part of your repos and install all the codecs:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by aces170 on 2008-05-31
Ok now somehow I have managed to screw up things, its a wonder it lasted me 2 weeks

I had removed my ATI drivers from add/remove and tried installing an older set of drivers, which screwed up the entire OS... Since past 2 days I could not get Ubuntu to boot at all. In the recovery mode it used to come on the blue screen, which said repair packages, or x-driver etc and use to hard freeze.

Today somehow it logged onto the normal login, but my resolution was jacked up and I could not install the ATI drivers got the error attached in the screenshot.

Ok now I am unable to load up Ubuntu at all... in the recovery mode its hard locking too...

[[IMG]http://img230.imageshack.us/img230/77/screenshotcz4.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=screenshotcz4.jpg)

---

### Post by Pumalite on 2008-05-31
Ctrl+Alt+F1 to get command line:
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose vesa as the driver.
Then: startx

---

### Post by aces170 on 2008-08-30
Linux : Ubuntu 8.04 (Hardy version)

Video card from onboard ATI X1200 to NV 7900GTO

The screen resolution applet does not show any resolution over 640*480

Monitor: Old Samsung 17" CRT

The thing was 6 months back :) I screwed up linux OS by trying to install AMD gfx drivers by itslef. I never bothered with it, just gave it a try today with a VGA card (NV 7900GTO) I ran the upgrade command, and it downloaded some 212mb of upgrades and apps. I also installed the gfx drivers through the restricted drivers tab above, it downloaded and installed the NV drivers from the online repository. I was able to het the XORG config working too, but am yet stuck at 640*480 resolution at 50hz refresh rate :) When I run the xog.conf I get the foll screen:

[[IMG]http://img167.imageshack.us/img167/7150/xoggu8.th.png[/IMG]](http://img167.imageshack.us/my.php?image=xoggu8.png)

---

