---
title: "User-switch gives me a black screen and nothing else."
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by iomtalach on 2010-04-30
Login as myself, girlfriend wants to use her login to check something, all good.

I switch back to myself, I get a black screen with just my cursor. Most annoying.  I have to ctrl-alt-f1 to reboot. I've tried killing various process from the term, but nada. I've also tried uninstalling gnome-screensaver as was mentioned in another thread when I searched, but no joy there so far.

This makes daily use a little annoying. :) I miss ctrl-alt-bksp.

Anyone else run across this and have a solution, or other places to look?

---

### Post by mathias j sagartz on 2010-04-30
After I installed 10.04, on the first restart everything worked as it was supposed to.  After that, whenever I restart and select Ubuntu from the grub menu, things go bad.  The login window appears and accepts my login but all I get after that is the mouse pointer and the background.  No desktop.  If I right click the mouse a smallish box appears with 7 menu options.  These actually work.  If I click on the "create a file" option a window opens running gedit.  Selecting "change desktop background" brings up a window with sample backgrounds.  Ctrl-alt-del brings up a box with the
standard shutdown options. It's almost as if the desktop is there hiding behind the background.

Is this similar to your problem?  Booting into Windows from the grub options works.

---

### Post by iomtalach on 2010-05-01
Sounds similar, but I have no problem booting up and logging in. This only happens when switching users for me. I bet the issues have a related cause, though.

What a fun and curious bug!

---

### Post by OnlyTim on 2010-05-01
I think I found the solution. I had the same problem. I'm using KDE and Gnome together. I had no problem switching users on Gnome, but when I tried to switch from KDE, I got the black screen and had to reboot. 

I switched the login from kdm to gdm using a term command. I'm still sorta a newbie, but it worked.

Here's my thread.


[http://ubuntuforums.org/showthread.php?t=1466537](http://ubuntuforums.org/showthread.php?t=1466537)

---

### Post by skbhat03 on 2010-05-01
Do the following:

1. When you insert the CD and boot, you will get a screen with a small rectangle (keyboard) and a human figure at the bottom of the screen. When u arrive at that screen, just press any key, space bar will do.
2. You will get the language option, select English and press enter, you will be taken to a screen with options for installation.

3. Make sure the option "Try Ubuntu without any changes" is selected (don't hit enter yet)

4. Now press F6 on ur keyboard.

5. You will see a small pop up on the right hand side of the screen, just hit escape to make it go away. And you can see a long command line which is already there.
Just start typing 
i915.modeset=0 xforcevesa and press enter.

And from there it should work fine :)


Best regards,
Subbu.

---

### Post by mathias j sagartz on 2010-05-01
Didn't help me.  Booted with LiveCD but didn't get the human 
figure at the bottom of the screen.  I did get to the Try without changes screen with English selected.  Pressing F6 brought up nothing.  Darn!

---

### Post by WolverineFan on 2010-05-03
> **skbhat03 said:**
> Do the following:

1. When you insert the CD and boot, you will get a screen with a small rectangle (keyboard) and a human figure at the bottom of the screen. When u arrive at that screen, just press any key, space bar will do.
2. You will get the language option, select English and press enter, you will be taken to a screen with options for installation.

3. Make sure the option "Try Ubuntu without any changes" is selected (don't hit enter yet)

4. Now press F6 on ur keyboard.

5. You will see a small pop up on the right hand side of the screen, just hit escape to make it go away. And you can see a long command line which is already there.
Just start typing 
i915.modeset=0 xforcevesa and press enter.

And from there it should work fine :)


Best regards,
Subbu.

This did do something for me.  I had to boot to the CD a few times before my key presses were recognized and got me in to the text mode installer.

Also, when it tried to boot the live install it failed with something about low graphics mode.  I just shut the computer down at that point, took out the CD, and started Ubuntu normally.  

No more black screen during the first or second user switch.  However, now it happens at the 3rd user switch (A -> B -> A works, then -> B fails)

Probably unrelated, but when I started up after using the CD the first time, my network wouldn't come up.  A reboot fixed that.

Is there a bug report for this yet?  I can't find one... 
[https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet](https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet)

---

### Post by Pilo on 2010-05-03
newbuntuxx and I are having a similar problem over in [http://ubuntuforums.org/showthread.php?t=1471915]("http://ubuntuforums.org/showthread.php?t=1471915")

---

### Post by WolverineFan on 2010-05-04
I filed a bug report.  Feel free to chime in with your individual details.

[https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/574909](https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/574909)

---

### Post by hrocks on 2010-05-04
After recent upgrade to kubuntu 1004, if I log out from my X session I never get the kdm login screen back.  All I get is a black screen.  I've tried CTRL-ALT F1 and typing commands blind but get no response.  If I hit the power button it does a clean power down within a few seconds.

A workaround I've found.  If I want to change users I can CTRL-ALT-F1 and run 'sudo service kdm restart'.  This kills the first Xsession user and is immediately followed by the kdm logon screen.  *BUT* if I do any CTRL-ALT-F1-6 and then CTRL-ALT-F7 I get boot messages instead of the X terminal window and X is no longer usable until I do the 'service kdm restart' again.

---

### Post by SentientFluid on 2010-10-12
I was having a similar issue in 10.04 where I was able to switch users just fine, but if I tried logging out of any user then I hung at a black screen. It was a bug with the 173 nvidia drivers and the fix was to install the 173 drivers used with 10.10.

The steps I used can be found here: [http://ubuntuforums.org/showpost.php?p=9963115&postcount=35](http://ubuntuforums.org/showpost.php?p=9963115&postcount=35)

---

