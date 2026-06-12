---
title: "Problem starting x when installing 8.04"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by jacksmash on 2008-05-08
Hi,

First-time poster here.

I've been able to search and find many threads about this problem, and I've tried about everything that's been suggested.

Basically, when I run the install disk for 8.04 (i386), the x-server fails and I get an error like:

"Fatal server error: no screens found"

I've tried reconfiguring xorg.conf, manually entering 'vesa', etc... but no luck. Some threads suggest there is no fix to this problem, but I thought I'd check anyhow. Perhaps I should try installing an older version of Kubuntu?

My specs:
LG laptop (E200)
Win XP  on one partition
ATI Radeon X1250 card
etc

I would appreciate any suggestions.

---

### Post by bobnutfield on 2008-05-08
This error can occur when your xorg.conf file has vertical and horizontal numbers outside the range of your monitor.  You might try making a back-up of your xorg.conf file and then change these number to a lower number, as well as checking the refresh rate.  This is the section to look in:

> Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option		"Defaultdepth"	"24"

Also, try running:

> sudo dpkg-reconfigure -phigh xserver-xorg

If that doesn't help you:

> sudo grep EE /var/log/Xorg.0.log

This will give the errors that the kernel is encountering when trying to start X.

Bob

---

### Post by jacksmash on 2008-05-08
Thanks for the reply.

The Screen section of my xorg file reads:

Section "Screen"
  Identifier "Default Screen"
  Monitor "Configured Monitor"
  Device  "Configured Video Device"
EndSection

Then, after I try to reconfigure (as you suggest), I get the same thing. I try to reconfigure again without the '-phigh' option, and get the same thing (each time trying to restart using 'startx').

I have tried all of this already, but did it again just to be sure.

Also, 

```
sudo grep EE /var/log/Xorg.0.log
```

Yields:

(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration.



Any thoughts?

---

### Post by bobnutfield on 2008-05-08
I am running 8.04 with a Toshiba A210 and an ATI X1200.  The section of my xorg.conf that I posted is identical to yours except for the defaultdepth.  You might try adding those lines (after making a back-up).  Also, the errors from the log file suggest that no driver at all is being found.  Have you tried to install the fglx driver with Synaptics.  You indicate that you have tried all of this, so I am assuming you have already tried the ATI driver, but thought I would ask anyway.

If these things don't work for you, this is the sum total of what I know to fix this find of problem.  I did in fact have this problem a long time ago with a Fedora install, and installing an updated non-free drive fixed it for me.  Hopefully, someone with more knowledge will post an answer.

Bob

---

### Post by jacksmash on 2008-05-08
Bob,

I apologize for my over-generalization. I definitely have not tried everything - but rather, just everything I've found as I've researched this problem. Of course, I'm sure there are things I've not found.

The answer to your question about the ATI driver, is no - I have not tried installing it. I'm not even sure how I would go about doing that seeing as how I haven't even started the install process for the OS itself yet.

I'll try modifying the xorg file according to what you said and report.

Thanks for your patience.

---

### Post by bobnutfield on 2008-05-08
Oh, I see.  I misunderstood.  I thought you had installed and could not get a desktop screen and was working from a text login.  So you are getting these erros from trying to run the live cd or the install disk?  If you are trying to install from the install disk, you can install in text mode and then sort out the driver once Hardy is installed.

Post which one you are getting these errors from.

Bob

---

### Post by jacksmash on 2008-05-08
Hmmm... this will show how much of a noob I am - but what's the difference between the live cd and the install disk? Is the live cd where you actually run the OS from the cd itself, and then install? If so - that's not what I'm doing. I simply select a graphical install at boot and then go from there.

---

### Post by bobnutfield on 2008-05-08
OK, now I understand.  You can install the operating system in text mode and it will install.  The dpkg-reconfigure -phigh command will probably sort it out for you once it is installed.  The live cd is in fact running the operating system from the cd and there is an option on the desktop to install.  But if you are using the normal install cd, you may have to install in text mode.  If you are new to linux, this may be a little more complicated, but not much.  You simply follow the instructions during the install.  The tricky part is if you are going to dual boot with windows, you must partition your hard drive and you must be careful here not to wipe your windows installation.  If Ubuntu is going to be the only OS on the system, then it is straight forward and quite easy.

Bob

---

### Post by jacksmash on 2008-05-08
Ok, thanks Bob - I'll give that a shot. I just reinstalled Windows anyhow - so everything's already backed up. I'll report back after I've given it a shot.

---

### Post by bobnutfield on 2008-05-08
OK, but I am curious were the results from the commands you tried are coming from if the OS is not yet installed.  Is this from the command line of the install cd?

---

### Post by jacksmash on 2008-05-08
Yes. When the install would start, x would crash. I would press CTRL+F1+F2 to get a command line.

Ok... I've installed in text mode. I've tried all of your suggestions above but X still won't start.

Do I have to install an ATI driver from the command line?

---

### Post by bobnutfield on 2008-05-08
Do you have a network connection?  If so, type:

sudo apt-get install fglrx-amdcccle

sudo apt-get install fglrx-kernel-source

sudo apt-get install fglrx-control

This will require that you are connected to the internet.

If not, try the previous xorg reconfigure commands now that you have a full install.

Post back the results

Bob

---

### Post by jacksmash on 2008-05-08
Ok... I got it working. I just followed the instructions here:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

Thanks for your help bob!

---

### Post by jacksmash on 2008-05-08
> **jacksmash said:**
> Yes. When the install would start, x would crash. I would press CTRL+F1+F2 to get a command line.

Ok... I've installed in text mode. I've tried all of your suggestions above but X still won't start.

Do I have to install an ATI driver from the command line?

> **bobnutfield said:**
> Do you have a network connection?  If so, type:

sudo apt-get install fglrx-amdcccle

sudo apt-get install fglrx-kernel-source

sudo apt-get install fglrx-control

This will require that you are connected to the internet.

If not, try the previous xorg reconfigure commands now that you have a full install.

Post back the results

Bob


Oh.... I just saw this post now. Will I be okay using the method I just posted a link to?

---

### Post by bobnutfield on 2008-05-08
Yes, those instructions will get you going.

Bob

---

### Post by bobnutfield on 2008-05-08
Use the instructions in that post, not what I posted.  

Bob

---

### Post by jacksmash on 2008-05-08
Ok - I've done that. But now, whenever I try to log out, I get an error that takes me back to the command line again. When I startx, I get the gui again.

Here's the error:

"waiting for X server to shut down
(EE) fglrx(0): [drm] failed to remove DRM signal handler"


:S

---

### Post by bobnutfield on 2008-05-08
There are many posts with this problem among people using the ATI driver.  If you can get back into the desktop and go to System>Administration>Synaptic and search for a program called EnvyNG.  This is a program that will install the correct driver for your graphics card and automatically update you xorg.conf file.  If this doesn't correct it, you may need to use the open source drivers, but will not get as good a performance from them.

First, though, go to System>Adminstration>Hardware drivers and make sure that the driver is enabled.  As I mentioned, there are a lot of threads on this forum from prople ATI cards with this same problem.  This may help if you need to install a different ATI driver:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method")

Bob

---

### Post by jacksmash on 2008-05-08
Ok, I will look into this. The thing is, I can tell the driver is installed correctly. Running fglrxinfo shows the ATI drivers, and get good framerates running glxinfo. I can't see how the wiki article you linked to will help me... but I'll do some more searching around, try out EnvyNG, etc. and will then report back.

Thanks

---

### Post by jacksmash on 2008-05-08
Thanks again Bob. I got it all working fine with EnvyNG.

Cheers.

---

### Post by bobnutfield on 2008-05-09
That's great.....ATI can be a booger sometimes.  Glad all is OK now

Bob

---

### Post by jacksmash on 2008-05-09
Now that my graphics issue is solved, I still find that my system is somewhat unstable. When I try to reboot/shutdown, sometimes it works, sometimes it doesn't. I'm going to do some searching on that to see what I can come up with. Perhaps the laptop I'm using simply isn't the best, since it's designed for Vista (I even downgraded to XP since Vista is such a hog).

Anyhow, can someone tell me how to edit the thread title so I can show that my original issue is solved?

Thanks again to Bob for everything.

Cheers.

---

