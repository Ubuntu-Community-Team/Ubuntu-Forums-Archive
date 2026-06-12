---
title: "[SOLVED] Unable to burn installation disc"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by JMuffin on 2008-09-05
I've been trying to download and burn an Ubuntu Installation disc to use on an old laptop. I have downloaded the ISO and have tried three different burning programs on three different machines and every time I try to install I get a  disc read error and a window telling me to reboot. I was going to try installing from a usb drive but there seems to be no way to change the boot order on the laptop so that's not really an option. I tried downloading ans installing Xubuntu and that works fine. Has anyone else experienced anything like this?

---

### Post by rihannaisco on 2008-09-05
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by zvacet on 2008-09-05
Did you checked [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") and disc integrity if md5sum was correct?In other hand if it is old comp maybe Xubuntu is right choice.You can replace Xubuntu desktop with Ubuntu one following instructions [here.]("http://psychocats.s465.sureserver.com/ubuntu/puregnome") Read under **Remove Xubuntu**.

---

### Post by JMuffin on 2008-09-05
I just ran md5sum and the hash matches. I've tried checking the cd for defects on multiple machines after I burn it. On my desktop which is currently running Ubuntu, I start the check and after a little while I get the disc read error. On my girlfriends desktop which is running windows, I actually got one copy to get to 100% on "Loading Linux Kernel" (or something similar. the first part of checking the disc) and then the whole thing froze. On my newer laptop which is running windows I get the same result as my desktop. I have also now tried downloading and installing Linux Mint and am getting the same results. It basically seems that Xubuntu is the only distro I am able to successfully burn and run in any of the machines in my house. The laptop I am trying to install to isn't really even that old. Is it possible that it has something to do with the actual media I'm using? Should I run out and buy a couple blank CD's of a different brand to see if I have better luck?

---

### Post by gkestrel on 2008-09-06
First try checking the md5sum of the iso that you downloaded to rule out a corrupted download, if it fails then do a fresh download and check that. If the iso file passes the md5sum check then the problem has to be one of the following:

1. The way the cd has been burned, have you burned the iso correctly by burning an image file, did you burn at the slowest speed possible, did you verify the disk after burning it, some burning software will do it for you if you tell it to, and also verify the md5sum of the burned disk.

2. Possibility of a dirty lens in your drive, try running a cleaning disk in it to see if that helps, or if the drive is getting on it may be starting to fail on the burning side of things.

3. The actual media you are using makes a big difference try and use good quality media whenever possible.  There could be many different problems here, bad or ageing media, your drive not liking the media you are using, So trying different media here would be a very good idea.

4. The drive in the laptop you are trying to install on may be dirty or failing, again try a cleaning disk in it.

try those things first and see if it helps if not post back and we will try and help you out further.

---

### Post by JMuffin on 2008-09-06
It appears that the CDs I had were just complete and utter crap. Bought a new spindle and burned the same image I had already downloaded and everything is working great. Thanks for the help!

---

