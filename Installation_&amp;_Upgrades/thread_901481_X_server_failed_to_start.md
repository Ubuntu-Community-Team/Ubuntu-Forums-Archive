---
title: "X server failed to start"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by Scottla on 2008-08-26
Oh, was it running so sweet under 7.04.  Why I hit the Upgrade 7.10 button this morning I'll never know...

Anyway, it went through the auto install process almost all the way through, then I got a BUNCH of "can't install" notifications with only an "OK" option.  Clicked through them, then rebooted the system and now Ubuntu won't boot up.

It goes about halfway thru the start up routine (pretty logo and orange bar), then kicks out to text and eventually ends up at:

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose problem? <YES>"

YES leads to:

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Buiold Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dsfg-12ubuntu8.4)
Current Operating System: Linux ubuntu-desktop 2.6.20-17-generic #2
SMP Wed Aug 20 16:47:34 UTC 2008 i686
Build Date: 13 June 2008
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from the config file, (==) default setting, (++) from the command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) log file: "/var/log/Xorg.0.org", Time: Tues Aug 26 13:26:04 2008

I am in way over my head here.  I'd prefer not to have to do a fresh install as I had the PC running just so, had several custom apps, and a lot of personal files on board.

Any help, suggestions appreciated.

---

### Post by Pumalite on 2008-08-26
Get into Recovery Mode and do:
dpkg-reconfigure xserver-xorg
Accept most defaults; choose vesa as the driver
Once in the system, update it and later install appropriate driver.

---

### Post by Scottla on 2008-08-26
Thanks for the prompt reply.

Did so.  Got...

"xserver-xorg is broken or not fully installed."

That doesn't sound good.  What next?

---

### Post by Pumalite on 2008-08-26
Get into Recovery Mode and do:
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
Then try configuring your xserver if you don't get it with the upgrade.

---

### Post by Scottla on 2008-08-26
Pumalite, thanks so much for your posts and clear sytax instructions.  I am not at that computer anymore, but will be back tomorrow.  I'll try your recommended fix tomorrow morning and get back to you with results.  Do keep a look out in case there's more to this story!

---

### Post by Scottla on 2008-08-27
OK.  Ran the process, rebooted and presto, my PC is back.

Thanks again for the quick and accurate help.

---

### Post by fwankyvii on 2008-08-31
Thank you so much! I just installed ubuntu 2 days ago and it told me that there were like 218 updates ready to install so I installed them and my kernel got changed and I didn't know what the hell to do because I don't know anything about the terminal at the moment so when that happened I was dead in the water, and then I did what you said and it worked!

Btw nice forum, I hope to come here often now that I have the best OS.

---

### Post by Pumalite on 2008-08-31
You are welcome guys. Good luck!

---

