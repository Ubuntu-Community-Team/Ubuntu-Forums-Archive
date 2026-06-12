---
title: "Video out of range, system paralyzed after 12.04.1 upgrade"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by pwabrahams on 2012-10-12
After upgrading one of my machines from Kubuntu 12.04 to Kubuntu 12.04.1, the system is very ill.  After the *hardware* bootup screen, the video goes out of range and never gets to display the boot menu.  After a while  it brings up the login screen.  But after I log in, the system is pretty much paralyzed in a manner suggesting that a serious CPU hog is taking control.  I thought I might be able to fix the problem from a terminal, using Ctl-Alt-F1, but when I try that I again get the video out of range problem.  If I could invoke **startupmanager** I might be able to do something, but the system is so ill that I can't get it to start, neither from Alt-F2 nor from a konsole screen.  (konsole is displayed but I can't type anything into it.)

I think the only way I'll be able to fix this is to boot a rescue system, mount the partition containing the ailing system, and editing the file in the boot configuration that determines the video mode for bootup (splash screen and such).  But what file do I need to edit?

Update: by booting into the failsafe version of Plasma, I was able to recover my system.  But the virtual consoles (alt-F2, etc.) still cause a Video Out of Range error on my monitor.  The same thing happens on a restart.

---

### Post by efflandt on 2012-10-13
Just curious what you mean by "upgraded" Kubuntu 12.04 to Kubuntu 12.04.1?

I have not run Kubuntu for awhile, but if you regularly updated 12.04 it should have been the same as 12.04.1 when it was released.  If you tried to somehow force 12.04.1 after subsequent newer updates, I am not sure what would happen, especially without knowing what you actually did.  You might have disturbed updates newer than 12.04.1.

What video hardware do you have and what video driver version if not a default driver included in the system?

---

