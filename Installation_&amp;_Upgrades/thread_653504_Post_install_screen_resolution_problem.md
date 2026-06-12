---
title: "Post install screen resolution problem"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by MykeBuntu on 2007-12-30
First time in...Hello all... Pretty much a complete LinuxIdiot(tm) but have played for the last few weeks with the boot cds of Ubuntu and Mythbuntu

PROBLEM: I cannot change screen resolution in the gui after setting "advanced visual effects". I rebooted as prompted, but now CTL ALT (+/-) do not work any more. I suspect there is some magic from the terminal (CTL ALT 1) screen to fix it but that's a guess.

DETAILS: I just installed 7.10 to a brand new machine; the ultimate plan is to run Mythbuntu and use the box as a pvr. For testing purposes I have installed the Ubuntu 7.10 before trying Mythbuntu-- since I don't have an Hdhomerun yet.

When starting and at the login screen-- the display is scrambled. I have to CTL ALT +- to get a readable login screen. 

I went into the preferences I think (sorry- I cannot see it now!) and set the screen to 1024x768x60hz, and it accepted it.

So far, so good... 

I didn't reboot or restart X after that (maybe that was my mistake) and then I noticed the "set advanced visual effects" choice and selected it. It installed (a package?) and prompted for reboot. I rebooted, and now I am at the login screen-- but it's scrambled and CTL ALT +/- don't work any more-- the resolution does not appear to change. I am using the db15 out to connect to a (museum piece) Sony CPD-1304 14" monitor. It will run at 1024x768. 

While I would also like to resolve the "while loading" resolution-- and the "starting resolution in the gui"-- right now the bigger problem is that I cannot change the (scrabled) resolution in the gui-- I already tried CTL ALT BKSPC to restart X but it still does not work.

Reinstall from scratch *is* an option since I may ultimately install MythBuntu over this machine when I get the HDHR.

---

### Post by MykeBuntu on 2007-12-30
I found the CRITICAL answer-- I now have a readable screen to login to:

from: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
md5sum /etc/X11/xorg.conf |sudo tee /var/lib/xfree86/xorg.conf.md5sum
sudo dpkg-reconfigure -plow xserver-xorg

When it asks about the monitor do not let it autoconfig.
For the SONY CPD-1304, the pertinent details are
Horizontal refresh:	28-50
Vertical refresh:	50-87

I ran through the config-- and only changed the H/V refresh rates. The login page comes up in a readable format-- so I don't have to CTL ALT +/-. BUT now I have 2 new questions along this topic:

1. I *think* the monitor normally runs at 60hz refresh rate when at 1024x 768. But In "Screen Res. Preferences" it shows it's running at 50 hz with an option for 53 hz. I've never seen it run that low before; is there a place to set that in xorg.conf that I didn't notice?

2. As I said-- the login page is now displaying correctly. But the splash screen with the Ubuntu logo (and fuel bar) is still in a wacky resolution/refresh rate. I suppose there's another text file somewhere to alter, but don't know where to look.

**[COLOR="Green"]ADDENDUM[/COLOR]** (I figured adding to this message was a better way to do this than posting a SECOND reply to myself) 
First, I guess I should ammend my description of myself...I am a **_BIG IMPATIENT _**LinuxIdiot(tm). Resolved the splash issue by following these directions: [http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html](http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html) . The reason I was getting scrambled display on the splash is that out of the box, Ubuntu fires it up 1280x1024 resolution... which my dinky 14" monitor does not support.

---

