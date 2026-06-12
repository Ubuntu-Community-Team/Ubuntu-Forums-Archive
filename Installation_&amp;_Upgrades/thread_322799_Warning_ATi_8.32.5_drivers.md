---
title: "Warning ATi 8.32.5 drivers"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by jgcamp99 on 2006-12-21
OK, before I tell you they break Edgy Eft, I'll ask if anyone has gotten them to work ?

I tried 3 times tonight and each time I had to downgrade back to 8.31.5.

First, followed the manual wiki instructions like I always have for every upgrade version that has worked with success prior to 8.32.5.

The openGLoverlay continues to be set to "off", so ATi/AMD hasn't fixed that. I manually correct that in the xorg.conf file. Afterwards, my system is a hopeless series of lockups and crashes in hopes to get a failsafe gnome boot in recovery mode using gdm that gives me a single shot at downgrading to 8.31.5. I finally get this to happen. 

Then I go to the updated wiki and there are new instructions on how to manually do this. So the first couple times, I have to figure it's because the old wiki doesn't apply and it was all my fault. But at least with those attempts I was eventually allowed to run GDM as root in failsafe gnome of recovery mode. So with the new wiki instructions I follow them strictly. Cut and paste into the xterm session, so there are no typos on my part. The results, same openGLoverlay turned "off" and the subsequent reboot hoses gdm completely. I can't even get gdm to initialize in failsafe gnome under recovery mode. Fortunately I wrote the instructions down for installing 8.31.5 and under recovery mode, I manually type in the commands one by one at the command prompt. That was my only hope at that point, glad it was an option available that still worked. This restores my system, but I know openGLoverlay is still turned "off" in xorg.conf. So I am able to eventually get that safemode recovery mode to boot and fix that. Edgy is fine now, that it is back on 8.31.5.

So my warning is, there's a good chance 8.32.5 will hose your system like it did mine.

I couldn't say whether 8.32.5 is any good, it doesn't install. On the wiki there is a couple of lines of code that indicate 8.32.5 is/may be broken.

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

"Fix a possible error:

sudo mkdir -p /usr/src/modules/fglrx/linux
sudo touch /usr/src/modules/fglrx/linux/config.h"

nothing possible about it, after 3 attempts there is an error with 8.32.5. If you've got a few hours to waste, upgrade to 8.32.5, but eventually you'll wind up back w/ 8.31.5 anyway.

---

### Post by missingxtension on 2006-12-27
well actually you saved mu hide yesterday i was up till 5:30a trying to install this shiat ](*,) 
and i had to be at work at 8a so today at 2.30a i found the answer and thank you very much the module builds and installs now no more linux/config.h missing 
im about to reboot into the drivers now but they seem to compile just fine 
thanks a bunch man i promise i will repay this by going to the irc channel and helping more often

---

