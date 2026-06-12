---
title: "Dead In The Water After Upgrading To Karmic"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by Windows Refugee on 2010-01-24
I had Ibex installed for about a year, and upgraded about a week ago to Jaunty (did an upgrade, not a full re-install).  Then I upgraded once again to Karmic, today (again, an upgrade, not a full reinstall).

That raises the question... Did I have to upgrade to Jaunty first, or would it have been possible to upgrade directly to Karmic from Ibex ????

The upgrade to Karmic appeared to complete successfully, but a reboot left me with a blank screen, and (apparently) the CPU running at 100% utilization (based on the fans sounding like the machine was about to blast off).  There was absolutely no hard disk activity.  I tried rebooting several times, with the same results.

Rebooting in recovery mode does get me to the terminal, where I can enter commands.  Rebooting normally (using any of the three kernels available to me) hangs the machine.

So, I downloaded Karmic from ubuntu.com, and burned a CD.  Booting off the CD produces the same result.... nothing !.  It does ask me to choose my language, but then after I try to load Karmic, I get a blank screen with no disk activity.

Machine is a Compaq Presario laptop with an AMD Athlon CPU, ATI video adapter and 512MB RAM.

Is there anything I can look for in a log file to help me understand what's happening ?    Any suggestions as to changes I can make from within grub, to try and get it to boot ?

Thanks !

---

### Post by jdeca57 on 2010-01-24
Perhaps only a video problem? What happens when you press [Alt-F2]? If you get a login screen, I'd go for the vesa solution, see: [http://ubuntuforums.org/showthread.php?t=1328465](http://ubuntuforums.org/showthread.php?t=1328465)

---

### Post by Windows Refugee on 2010-01-24
> **jdeca57 said:**
> Perhaps only a video problem? What happens when you press [Alt-F2]? If you get a login screen, I'd go for the vesa solution, see: [http://ubuntuforums.org/showthread.php?t=1328465](http://ubuntuforums.org/showthread.php?t=1328465)

I'll try Alt+F2, but I doubt it will do anything.  Based on the fact that I'm not seeing any disk activity when the OS should be loading, I'm pretty sure that nothing is getting loaded.

BTW, I have tried all of the F6 options when booting from the CD....  noacpi, acpi=off, etc.  Nothing helped.

---

### Post by darkod on 2010-01-24
Sound like video problem with ATI. I had something similar with Karmic and my onboard HD3200. Boot the recovery mode option, and in the next menu select something like "root with networking" to give you internet access.

After the command prompt loads, install video driver handling package EnvyNG with:
sudo apt-get install envyng-core envyng-qt

Run it in text mode with:
envyng -t

Select ATI driver from the menu (no need to remove current one, I didn't), it will download the correct one and install it. Just follow the messages. After all is done, it will ask to reboot, and it should work if you select the normal mode entry this time.

---

### Post by kansasnoob on 2010-01-24
> would it have been possible to upgrade directly to Karmic from Ibex ????

No.

This certainly sounds like an Xorg problem and the answer to my Karmic Xorg issues, although different than yours, was to give up on Karmic. Sad I know but that's just what I said in the bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/475010/comments/17](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/475010/comments/17)

I simply could not risk hardware damage at this time.

So if Jaunty worked well for you I'd suggest burning a copy of Jaunty and reinstalling. Of course, unless you have a separate /home, you'll have to create a backup (always a good idea anyway) and restore all of your data.

Or, if you're really brave, you could try Xorg-edgers but be mindful of this:

> Packages **for those who think development versions, experimental and unstable are for old ladies**. We want our crack straight from upstream git! Well, straight, we want it built and packaged so we don't need to know what we're doing, except that **we will break our X and put our computers on fire**.

[https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers)

The PPA is here:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

This might even be interesting:

> == New in Karmic ==

Radeon r6xx/r7xx 3D support. Install a 2.6.32 kernel or newer from the Mainline Kernel PPA or from lucid. Mesa is following 7.7 branch, and might be updated to 7.8 after 7.7 is pulled into lucid officially.

---

### Post by Windows Refugee on 2010-01-24
Well, I tried booting Karmic again...

When I got the blank screen and no disk activity, I pressed ALT + F1, and the screen turned GREEN.  Then I saw that there was disk activity.  It was indeed booting, but an error popped up saying that...

UBUNTU IS RUNNING IN LOW-GRAPHICS MODE

THE FOLLOWING ERROR WAS ENCOUNTERED

(EE) NO DEVICES DETECTED


This certainly appears to be a video adapter issue with Karmic on my Compaq laptop.

So, I let it finish booting, and to my surprise, it let me log in, but it was not able to display my desktop.  Unfortunately, I can't get my tethered Internet connection working under the circumstances, so I could not install "envyng-core", as was suggested. 

I'm not sure what, if anything, I can pursue at this point to try and solve the problem with Karmic, short of reinstalling Jaunty !!!    ...And I can't submit a bug report from that machine if I don't have Internet connectivity !

---

### Post by darkod on 2010-01-24
> **Windows Refugee said:**
> Well, I tried booting Karmic again...

When I got the blank screen and no disk activity, I pressed ALT + F1, and the screen turned GREEN.  Then I saw that there was disk activity.  It was indeed booting, but an error popped up saying that...

UBUNTU IS RUNNING IN LOW-GRAPHICS MODE

THE FOLLOWING ERROR WAS ENCOUNTERED

(EE) NO DEVICES DETECTED


This certainly appears to be a video adapter issue with Karmic on my Compaq laptop.

So, I let it finish booting, and to my surprise, it let me log in, but it was not able to display my desktop.  Unfortunately, I can't get my tethered Internet connection working under the circumstances, so I could not install "envyng-core", as was suggested. 

I'm not sure what, if anything, I can pursue at this point to try and solve the problem with Karmic, short of reinstalling Jaunty !!!    ...And I can't submit a bug report from that machine if I don't have Internet connectivity !

You mean your internet doesn't work if you select recovery mode entry and then root with networking?
If possible, connect using ethernet cable to your router/cable modem. Wired internet should work in most cases unless you have some specific setup to make your internet working. In that case I guess you're really out of luck. :(

---

### Post by Windows Refugee on 2010-01-24
> **darkod said:**
> You mean your internet doesn't work if you select recovery mode entry and then root with networking? 

That's correct.  My choices are dialup, using my laptop's internal modem or tethering to my cellphone.  I couldn't get either of these to work in Ibex, which was what inspired me to upgrade.  

I could try Wi-Fi, but I'm not sure I can get it working without being able to get to the desktop.  I have to be able to configure it for a WPA2-secured access point.    I'm posting this reply from the laptop in question, but only after booting into Windows.  ...in Windows, both Wi-Fi and tethering are working.  The other possibility is to take the laptop somewhere I can connect it by ethernet cable.

A apropos saying that comes to mind is...
     Water, Water Everywhere, And Not A Drop To Drink !

---

### Post by Windows Refugee on 2010-01-28
ENVY DIDN'T COMPLETELY SOLVE MY PROBLEM !

As darkod recommended, I installed "Envy Next Generation"...

    sudo apt-get install envyng-core envyng-qt

which took well over an hour to download from us.archive.ubuntu.com.  Despite being connected to a 6 Mb/s cable modem by 100 Mb/s ethernet (I did a speed test to verify), the files (around 60 Megabytes worth)transferred at dial-up modem speed or slower.  Not sure if it's something on my end or not, however, everything did eventually download, and the install appeared to complete OK.

Then I ran Envy with...

     envyng -t

and I selected the ATI driver, since that's my machine's video adapter.  Downloading the driver took almost a half hour to complete.  Then I selected the reboot option.

BUT, the same problem still exists...  When booting, if I select a normal boot in Grub, machine appears to hang and disk activity ceases.  But when I press ALT + F1, I get a GREEN screen, and the booting proceeds in the terminal window.  I still get the "(EE) no devices detected" error.  However when I choose to continue in low-resolution mode for the current session, I do get to the desktop, which appears to be displaying/functioning correctly.

Any ideas why the machine still refuses to boot to the desktop on it's own, or why I still get the same error ?

---

### Post by Windows Refugee on 2010-01-28
BTW, Envy installed the following ATI graphics adapter driver...

8.660-0ubuntu4

---

### Post by darkod on 2010-01-28
That's the same driver that was installed for my HD3200 and it resolved my issue (which was slightly different to yours). I have no idea and it seems not to be the driver itself.
I don't know ubuntu that good yet. Maybe if you keep googling that error until someone jumps in.
Or even create another thread with the specific error/behavior in the subject line, it might attract someone.

---

### Post by Windows Refugee on 2010-01-29
Thanks again, darkod !

I'll repost this issue as you suggested.  I'm also considering erasing the partition and doing a clean install, to see if that makes any difference.  It seems strange, because I never had a problem with Intrepid or Jaunty on this laptop.  My problems started after the Jaunty to Karmic upgrade.

I did try booting Karmic from the live CD, but that presented a different problem on this machine.  I got to the desktop, but the screen would not behave correctly, with windows failing to disappear when they were closed, or failing to completely display when they were opened.  The more I tried to do, the more messed up the desktop became.  Sort of reminded me of some problems that are common with that other operating system that my rich uncle Bill sold me.  It made trying to work from the desktop impossible, so I gave up ](*,) on using the Ubuntu live CD.

---

### Post by darkod on 2010-01-29
> **Windows Refugee said:**
> Thanks again, darkod !

I'll repost this issue as you suggested.  I'm also considering erasing the partition and doing a clean install, to see if that makes any difference.  It seems strange, because I never had a problem with Intrepid or Jaunty on this laptop.  My problems started after the Jaunty to Karmic upgrade.

I did try booting Karmic from the live CD, but that presented a different problem on this machine.  I got to the desktop, but the screen would not behave correctly, with windows failing to disappear when they were closed, or failing to completely display when they were opened.  The more I tried to do, the more messed up the desktop became.  Sort of reminded me of some problems that are common with that other operating system that my rich uncle Bill sold me.  It made trying to work from the desktop impossible, so I gave up ](*,) on using the Ubuntu live CD.

That might actually mean there is an issue with displaying properly. If the live desktop is giving you headaches, the installed OS will most likely do the same. Just out of curiosity, are you willing to test the 10.04 Alpha? You can find daily build images here:
[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

It's only in Alpha so installing as main OS is not what you want, but you could check if it's running the live desktop better. For example, my issue with 9.10 is resolved with 10.04 Alpha. Hopefully the OS will get even better come the final release.

---

### Post by Windows Refugee on 2010-01-29
> **darkod said:**
>  Just out of curiosity, are you willing to test the 10.04 Alpha? You can find daily build images here:
[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

I didn't know that Lucid was available as an Alpha release.  Sure, I'm willing to try it, and will burn a CD when I have some time.  Will also see if  [ my new post ]("http://ubuntuforums.org/showthread.php?t=1393502")turns up any solutions.

---

### Post by recluce on 2010-01-29
I avoid using Karmic where possible, but I had one laptop already installed with Karmic, that had issues with the ATI drivers. Not as bad as yours, but suspend/resume crashed the machine.

Here is my guide on how to install Jaunty ATI drivers in Karmic:

[http://ubuntuforums.org/showthread.php?t=1371844](http://ubuntuforums.org/showthread.php?t=1371844)

All this should be doable from the recovery mode text shell with networking - and you might need a wired network connection. Alternatively, use another machine (or even windows) to download the files and copy them to your Ubuntu installation using a USB stick or some such...

---

