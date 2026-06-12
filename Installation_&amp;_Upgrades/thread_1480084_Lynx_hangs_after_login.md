---
title: "Lynx hangs after login"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by Pureferret on 2010-05-11
I've recently updated my Karmic install on the computer I use to Lynx, it all went through ok, expect perhaps it had to removed a fair few items, but I figured they were unsupported/out dated now so that would be ok.

When I login as my account (lets call it user), the purple splash (?) screen turns up for a second flickers and then goes black with the cursor showing 'busy' which after a minute at most goes to the normal cursor icon.

When I login as root the same thing happens expect it doesn't go black but hangs on the purple screen.

I've tried removing/uninstalling compiz, as well as pulseaudio which are some of the solutions I've found so far.

My uname is: Linux sliceY 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 X86_64 GNU/Linux

I have searched for this before but the only advise I found hasn't work or hasn't fitted my symptoms.

Thanks guys

---

### Post by Pureferret on 2010-05-12
After following some advice in various places on the forum (lots and lots of searching) I found .xsessions and wrote out some of the error messages. I'm hoping some of this will help someone explain whats wrong so I can fix it.

Some stuff from .xsession

```
(polkit-gnome-authentication-agent-1:1682):Glib-GObjectWARNING **:cannot register existing type '_PolkitError'

(polkit-gnome-authentication-agent-1:1682):Glib-CRITICAL **: g_once_init_leave: Assertion 'initialization_value !=0' failed to find a synaptics device.

(gnome-power-manager:1684):GLib-GObject-WARNING **:/build/buildd/glib2.0-2.24.0/gobject/gsignal.c:2273:signal 'proxy-satus'$gnome-panel:symbol lookup error: gnome-panel: undefineded symbol: GTK_widget_get_realized
nautilus: symbol lookup error: nautilus: undefined symbol: gtk_widget_get_realized
#This is repeated several times then a few breaks with errors such as:
(gnome-settings-daemon:1665):GdkPixbuf-CRITICAL **: gdk_pixbf_format_get_name: assertion 'format!=NULL' Failed
#More of 'nautilus: symbol lookup error...'
evolution-alarm-notify-Message: Setting timeout for 39845 1273622400 1273582915
evolution-alarm-notify-Message:  Wed May 12 01:00:00 2010

evolution-alarm-notify-Message:  Tue May 11 14:01:55 2010

Traceback (most recent call last)
 File "/usr/share/system-config-printer/applet.py", line 31, in <module>
  import pynotify
 File "/usr/lib/pumodules/python2.6/gtk-2.0/pynotify/_init_.py", line 1 in <module>
  from _pynotify import *
ImportError: could not import gtk
# *LOTS* more of 'Nautilus error'
**(update-notifier:2549): DEBUG:Skipping reboot required
# More of Nautilus
bluetooth-applet: Fatal IO error 11 (reseource temporarily unavailable) on X server: 0.0
#Silmilar error but with different apps: gnome-settings daemon, gnome-screensaver, Window manager warning, gdu-notification-daemon,gnome-power-manager,polkit-gnome-authentication-agent-1, gnome-session, evolution-alarm-notify, update-notifier, nm-applet.
```

---

### Post by StephenG on 2010-05-12
Same issue.  After "standard" upgrade from 9.10 through update manager, I get past the logon and to the regular desktop but nothing else comes up -- no bar at the bottom, no ability to right-click desktop, no nothing.  Already tried rebooting with same results.  I let it churn along for about 5 or 6 minutes before shutting it down.  I'm watching this thread for suggestions.

---

### Post by dino99 on 2010-05-12
maybe that:

When your computer is loading and Grub comes up, hit escape, and select the recovery mode option. When you get a screen asking what you want to do, select the option to drop to a shell. You can then work from there.

if you dont see grub menu, at the end of bios process, hold "shift" key down to see it.
You problably have a chipset issue (not recognized), give more info about your hardware

---

### Post by Pureferret on 2010-05-12
I just pressed a few random buttons and managed to get a 'save Print Screen' dialog to pop up. I don't think it's hanging just the desktop will not display. Someone suggested somewhere to run
```
sudo apt-get update && sudo apt-get dist-upgrade
```

Which I'm currently doing from a terminal, will edit-post results.

---

### Post by dino99 on 2010-05-12
also, goto system admin hardware driver to see if yours is activated

---

### Post by StephenG on 2010-05-12
Dino, are you talking to me or to pureferret?  Unfortunately, I am 1500 miles from home until Friday and can't work on that machine til then.  All the parts are less than 6 months old and 9.10 was working perfectly, so I doubt there are chipset issues.  For the time being, I'm doing my research for when I can get back to work on it.  Thanks for the quick reply.

---

### Post by Pureferret on 2010-05-12
> **dino99 said:**
> maybe that:

When your computer is loading and Grub comes up, hit escape, and select the recovery mode option. When you get a screen asking what you want to do, select the option to drop to a shell. You can then work from there.

if you dont see grub menu, at the end of bios process, hold "shift" key down to see it.
You problably have a chipset issue (not recognized), give more info about your hardware

I'm not 100% sure what a grub menu is, I've mostly taught my self linux and not seen one before. Unless it's a menu of OS to load? I only have one (OS) so that doesn't pop up. and I did read somewhere about holding shift but I've not gotten that to work, no matter where/when I press shift I don't get anything new to turn up.

How do I find the hardware info, please?:confused:

Ok I got the grub menu to pop up, I don';t know what that achieves as I can get to the command line with ctrl-alt-F2....

---

### Post by Pureferret on 2010-05-12
> **StephenG said:**
> Dino, are you talking to me or to pureferret?  Unfortunately, I am 1500 miles from home until Friday and can't work on that machine til then.  All the parts are less than 6 months old and 9.10 was working perfectly, so I doubt there are chipset issues.  For the time being, I'm doing my research for when I can get back to work on it.  Thanks for the quick reply.
Just like to echo Stephen G Who are you talking to?

The machine I had was running smoothly on Karmic (9.04), and the install seemed to go fine.

---

### Post by dino99 on 2010-05-12
> **StephenG said:**
> Dino, are you talking to me or to pureferret?  Unfortunately, I am 1500 miles from home until Friday and can't work on that machine til then.  All the parts are less than 6 months old and 9.10 was working perfectly, so I doubt there are chipset issues.  For the time being, I'm doing my research for when I can get back to work on it.  Thanks for the quick reply.

its not because 9.10 was working fine and had no chipset issues, thats mean 10.04 cant have issues with the same hardware ( = regressions), this forum is fullfiled with this kind of troubles sadly.

---

### Post by dino99 on 2010-05-12
> **Pureferret said:**
> I'm not 100% sure what a grub menu is, I've mostly taught my self linux and not seen one before. Unless it's a menu of OS to load? I only have one (OS) so that doesn't pop up. and I did read somewhere about holding shift but I've not gotten that to work, no matter where/when I press shift I don't get anything new to turn up.

How do I find the hardware info, please?:confused:

Ok I got the grub menu to pop up, I don';t know what that achieves as I can get to the command line with ctrl-alt-F2....

i've reread your posts and i think you have and issue with your graphic driver: can you check into: system admin hardware driver, if yours is activated, and what kind of graphic card you have.

lshw will list your hardware

---

### Post by StephenG on 2010-05-12
Sure,Dino, I realize that can happen but I was thinking optimistically.  So, being quite new at linux, would you mind giving me a list of commands to run so when I get home I can get on this project without further delay?  I suppose I'll need to start by entering the grub list at startup and see what's left there.  Then what?  I can't do anything from the desktop as there are no menus or even a menu bar, so everything will have to be command line I suspect.

fyi, I do not dual boot, so that's not an issue.  This is my son's school-work machine, used for his e-mail and schoolwork.  No special games or other stupid stuff.

---

### Post by Pureferret on 2010-05-12
> **dino99 said:**
> i've reread your posts and i think you have and issue with your graphic driver: can you check into: system admin hardware driver, if yours is activated, and what kind of graphic card you have.

lshw will list your hardware

I have done lshw but the list is so long and I have no way of getting it off of the machine.

I do know from previous experience that the machine has a intel Xenon processor and the graphics is a Radeon R100 QD (radeon 7200)

---

### Post by Pureferret on 2010-05-13
I've just noticed that my install lets me use the KDE desktop. I loads the blue screen, loads up a few icons (a HDD symbol, spanner, etc) it crashes on the lasto ne and then displays the strange message in a grey window.

Phonon: [B]KDE's Multimedia Library
[/B]The audio playback device** ALSA default output **does not work Falling back to .

Steve can you see if your son can replicate this?

---

### Post by Pureferret on 2010-05-13
I'm going to re install lynx over the broken (?) install.

See if that helps.

---

### Post by StephenG on 2010-05-13
He's 12 and I'm not there to assist him, so I'll wait until tomorrow night when I get home to try.  Also, since I upgraded from the update manager, I have no disc to try a reinstall until I download it from another machine.  I'm interested to hear if your reinstall does the trick.

---

### Post by Pureferret on 2010-05-13
> **StephenG said:**
> He's 12 and I'm not there to assist him, so I'll wait until tomorrow night when I get home to try.  Also, since I upgraded from the update manager, I have no disc to try a reinstall until I download it from another machine.  I'm interested to hear if your reinstall does the trick.

Fair enough. Will try to install it over night

---

### Post by dino99 on 2010-05-13
> **Pureferret said:**
> Fair enough. Will try to install it over night

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by Pureferret on 2010-05-14
Thanks, I've installed linux a few times but I'll bear that in mind. Will be installing today instead as I couldn't find a cd last night.

---

### Post by Pureferret on 2010-05-14
Re-install complete just waiting to log in now. I saved my display and hardware outputs to a disk though. I'm on I don't know what it was but something I had installed either had a dependency removed or was incomnpatible with something on there...?

---

### Post by Tholley on 2010-05-14
Just an observation on my part, but I think StephenG should have started his own thread. He said he had the same issue and would keep a watch on this thread, but seems to have hijacked it. Dino was originally trying to help Pureferret, and now just trying to read the posts, I'm getting confused on who is helping who.

---

### Post by StephenG on 2010-05-18
So, is it now working,pureferret?

Fine, tholley, I'll go elsewhere.  That way, we can all search a zillion threads instead of just a million, looking for answers.  Bye.

If you ever get it figured out, I'll be over here:

[http://ubuntuforums.org/showthread.php?p=9320837#post9320837](http://ubuntuforums.org/showthread.php?p=9320837#post9320837)

---

### Post by Carlos Pena on 2010-05-20
I have the same problem with the 32 bit version, so i agreed there is some chipset issues with 10.04.

There is a problem with the Video driver or Chipset issues for Intel 945GC. Ubuntu always hangs 3-4 minutes after login in normal mode. When you try selecting Gnome FailSave node option, Ubuntu seems to run better, but finally it hangs while you running a hardware test or any application. In other hand, i have several applications written in RealBasic that runs fine on 8.04, but they don't do nothing on 10.04 even in the console terminal. 
I have installed 10.04 from scratch several times with no better results. Now i am checking for updates everyday to see if some updates solve all those problems. I have other computers running 8.04, but i won't update them to 10.04 until this version work in my computer.

Carlos Pena
Santo Domingo, 
Dominican Replublic

---

### Post by Pureferret on 2010-05-20
This is not the same problem as the one I had. The screen would be black (nothing would render) but describing it as hanging is not wholly accurate. In my problem the mouse is moveable but I can't see anything but the cursor. Even Failsafe wouldn't let me see anything but a black screen.

You might get better replies form your own thread, Carlos.

Thanks

---

