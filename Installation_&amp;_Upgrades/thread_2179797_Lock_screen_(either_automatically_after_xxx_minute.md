---
title: "Lock screen (either automatically after xxx minutes or manually) with XScreenSaver"
date: 2013-10-09
forum: Installation &amp; Upgrades
---

### Post by ButchMel on 2013-10-09
I have installed XscreenSaver on Ubuntu server 12.04.3 (yes with desktop environment on top of it...).

I am reading that this is 'disabling' the lock screen command ( Ctrl + Alt + L ) and I also notice that the screen does not lock automatically either no matter how long it stays inactive (falling on screensaver).

Now if you wonder why I simply cannot live with the minimalist black screen of Gnome screensaver: my monitor has something really special that is, as soon as it goes to sleep, it shut down and it takes me 10 minutes pulling and plugging the power cord again and again before it powers on again... Don't ask...  So: no, Gnome minimalist black screensaver it *not* a viable alternative for me.

However, I found this :[http://www.jwz.org/xscreensaver/man1.html](http://www.jwz.org/xscreensaver/man1.html)  but have not tried yet the section that explains how to remove Gnome Screensaver, launch XScreensaver on startup then use the lock screen again.

I would definitely have the same I had under Ubuntu Server 10.04 LTS: have the system going to screensaver and screen locking after a specific time, just asking for password when I shake the mouse to stop the screensaver.  Is this the way to go, or is there something else I can do for this ?  (I am not that preoccupied by the Ctrl + Alt + L kind of manual lock-down)

Thanks,
B.

---

### Post by varunendra on 2013-10-10
Install "dconf-tools" if you don't already have it -
```
sudo apt-get install dconf-tools
```
then run "**dconf Editor**" from menu or dash, whatever you have. Navigate to - **org > gnome > desktop > screensaver**. In the right hand pane, you'll see options "**lock-delay**" (whose value is already set to "0" which is okay) and "**lock-enabled**". Make sure "**lock-enabled**" option is checked.

I don't have any screensavers installed to test this, but I hope this is all you need.

---

