---
title: "no GUI - Please help [resolved]"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by DavidTingdahl on 2007-02-10
After upgrading some packages (which I now don't remember the names of) I could not start up the GUI (X-Windows  suppose). all I get is a "grey" screen and the mouse pointer indicating that there is work going on. I can start in recovery mode but don't know what to look for since I am quite inexperienced with Linux.

Can someone please help me!

---

### Post by mikewhatever on 2007-02-10
Hi there,
I can not help you to solve the problem with the new kernel, since mine doesn't work too. You should still be able to use the old one, if you want to use the PC. Hopefully, the answer will turn up.

---

### Post by punkybouy on 2007-02-10
How about a re-install of Gnome or whatever desktop you were using?  I thinks it would be sudo spt-get install ubuntu-desktop.  I had to do it a few weeks ago

---

### Post by punkybouy on 2007-02-10
Sorry sudo apt-get install ubuntu-desktop.  KUBUNTU would probably be different.

---

### Post by DavidTingdahl on 2007-02-10
Thank you for the replies

in the Grub boot manager, I can choose from 
2.6.17-11-generic
and
2.6.17-10-generic

Both of them gives me the same results when starting the window manager so I cannot use Linux at all at the moment.

I tried also to re-installed the ubuntu desktop without any change.

Is there any simple way to uninstall the most recent package updates made so I can revert the system back to how it was before?

regards
David

---

### Post by sinister99 on 2007-02-10
I am having the same problems, wasn't there just an update to xorg?  Can't remember, but I get a blank screen with the mouse and can't do anything in a normal session.  The on the splash screen, only metacity appears now, no nautilus, etc.  Anyone have a fix?

---

### Post by hxx4 on 2007-02-10
I upgraded to 2.6.17.11 from 2.6.17.10 and now X doesn't start up. I'm currently using the old kernel which I selected in grub. The error message I got with the new kernel says that the wfb module failed to load, and there was an API mismatch with X module version 1.0-9746 and nvidia kernel module 1.0-8776.

---

### Post by Vorian on 2007-02-10
> **punkybouy said:**
> Sorry sudo apt-get install ubuntu-desktop.  KUBUNTU would probably be different.
Yes, It would be very different.:)

---

### Post by DavidTingdahl on 2007-02-10
I managed to start X-windows properly by pressing CTRL-ALT+F1 when the screen hung up.
From there I could log in with the console and start X-windows with the 'startx' command
Everything seems to work OK except that my ATI graphics drivers are not recognized any more.

It seems like simply X-windows is not starting properly with the startup script.

---

### Post by mikewhatever on 2007-02-10
> **hxx4 said:**
> I upgraded to 2.6.17.11 from 2.6.17.10 and now X doesn't start up. I'm currently using the old kernel which I selected in grub. The error message I got with the new kernel says that the wfb module failed to load, and there was an API mismatch with X module version 1.0-9746 and nvidia kernel module 1.0-8776.
It's such a great relief to have an ATI user with us. :lolflag: You're truly welcome. :)

---

### Post by DavidTingdahl on 2007-02-10
Finally I managed to recover completely by reinstalling my ATI graphics drivers
(I am using ATI 9700 mobility Radeon)

now everything works perfectly

---

