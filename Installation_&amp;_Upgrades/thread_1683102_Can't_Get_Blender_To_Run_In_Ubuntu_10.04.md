---
title: "Can't Get Blender To Run In Ubuntu 10.04"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by bry72 on 2011-02-07
Hey Guys,

I am having a problem getting Blender to run in Ubuntu 10.04.  Whenever I run it, it just gives me a blank grey screen.  I have to use "Force Quit" to close it down.  It will not close down just by right clicking on the bottom tab and choosing "Close".

I have installed the version from the Ubuntu Software Center and it gives me the blank grey screen.
I have manually installed version 2.49b with Python 2.6 for Linux x86-32 and it gives me the blank grey screen.
I have manually installed version 2.56a Beta, 32 bit and it gives me the blank grey screen.

I run a dual boot system with Windows XP and Ubuntu 10.04.  I have installed Blender in Windows XP and I have no issues.  The program opens and you can see the normal layout with buttons and such.

Here is my computer info:

Laptop Toshiba Satellite A100 (5 years old)
-Intel(R) Celeron(R) M processor   1.70GHz
-512 RAM (Although it shows Memory as being 432 Mib in sysinfo)
-Graphics card -  ATI Technologies Inc. RC410 (Radeon Express 200M)
-80 GB Hard Drive- 60 GB for Windows XP, 20 GB for Ubuntu 10.04  Currently 13.4 GB available in Ubuntu

I do not receive any error messages when I run Blender.  Just a blank grey screen opens up, doesn't allow me to do anything, shows no buttons and has to be shut down using "Force Quit".

Let me know if you need any more info about my computer.

---

### Post by kellemes on 2011-02-07
Open a terminal-window and start Blender from it..
Type 'blender' (probably) to start it.. now watch the output in your terminal-window.. post it if needed.

---

### Post by bry72 on 2011-02-07
Ok, this is weird.  I typed in blender like you said and it told me it could not be found. I  then realized I had uninstalled the last version .  It told me to type in sudo apt-get install blender, which I did.  I opened it and now it works.  I've had it open for 20 minutes now while using firefox and watching a movie all at the same time and it is still working.  I thought maybe having other programs open was the initial cause of the problem.

When I went back and typed in blender like you said, it gave me this message:  

Compiled with Python version 2.6.5.
Checking for installed Python... got it!

So for whatever reason, installing it through the terminal worked but installing it through the Ubuntu Software Center or manually causes issues.  Very strange.

---

### Post by bry72 on 2011-02-08
Well, it looks like I jumped the gun on saying my problem was fixed.  I tried opening the program later on and again I got the blank grey screen.  I uninstalled and reinstalled through the terminal but still the same problem.

I'm wondering if this has anything to do with the way I run Bleach Bit.  I run it in both normal mode as well as root.  I have both set up the same way:

Under Edit->Preferences I have a check mark ONLY on "Overwrite files to hide contents".
This then gives me a LONG list of programs from "Adobe Reader" all the way down to 'yum".
I have a check mark by ALL the boxes except for the following:
Epiphany - Places
Firefox - Places
Nautilus - History
System - Free Disk Space
System - Memory

I run Bleach Bit in both modes, first root and then normal, at least once a day.

Could this have anything to do with Blender not running?

As far as what it says now when I type the word blender in the terminal, it still gives the previous message of :  
Compiled with Python version 2.6.5.
Checking for installed Python... got it!

However, since it just gives a blank screen and I have to use "Force Quit" to close it down, it then gives me this message in the terminal:
X connection to :0.0 broken (explicit kill or server shutdown).

Not sure if that helps.

---

### Post by Bucic on 2011-02-20
[http://art.ubuntuforums.org/showthread.php?t=1684752](http://art.ubuntuforums.org/showthread.php?t=1684752)

---

