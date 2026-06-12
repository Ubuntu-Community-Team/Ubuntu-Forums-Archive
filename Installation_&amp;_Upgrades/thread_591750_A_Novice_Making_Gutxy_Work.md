---
title: "A Novice Making Gutxy Work"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by vanbob on 2007-10-25
After upgrading to Ubuntu 7.10 from Ubuntu 7.04 last Thursday (October18) using the Upgrade Manager, I had a series of problems that took a few days to resolve.  Since I am not a LInux guru but have had some success using Ubuntu Forums, I thought this account of my problems and solutions might be useful for others like me.

1.  Graphic Driver Problems.  I have Intel's 82945GZ (945) graphics.  After the update, the i810 driver was being used (it might well have been the driver before the update).  I changed "i810" to "intel" in /etc/X11/xorg.conf (using sudo gedit).  I also removed xserver.xgl (using Synaptic).  These changes seemed to fix a KDE (I normally use gnome, but was testing KDE) crash when selecting "Desktop" from the System Menu, a Google Earth startup crash, and (maybe) a crash trying to use Ubuntu's 3D desktop that I haven't been able to duplicate.

2.  Compiz Problems. I could not get any of the 3D Desktop graphics to work after the update.  Per a comment on Ubuntu Forums, I downloaded and built a LiveCD, used it, and it all worked!  Knowing that it can work, gave me confidence that I could make my updated system work, if I could determine the differences.  One big difference was Compiz was not getting loaded (per System->Administration->System Monitor).  From another Forum comment, I entered the 'compiz' command in a terminal and the desktop effects started to work.  An interesting problem occurred if I closed the terminal session, the windows borders disappeared (which was similar to another problem on the Forum).  After a reboot, I started 'compiz' in a terminal again and (from yet another Forum comment) I installed 'emerald' (using Synapitc -- I like Synaptic because I can easily find out what is installed) and I never stopped the 'compiz' terminal session.  After this, 3D desktop effects seemed to work great.

3.  System->Preference->Appearance Applet.  Tabs in this applet did not seem to work.  What actually happened was the screen was not written when a Tab was selected.  If you happened to hit the right spot for a button or control on the screen the appropriate action would actually occur.  This made it exceedingly difficult to work the problems mentioned above.  From another Forum comment, I removed gtk-qt-engine and this Applet started to work.

In summary, my initial impressions with Gutsy were negative with the crashes, desktop not working correctly, and the Appearance Applet being unusable.  However, all the issues I encountered were covered in the Forums.  It took some searching and experiments, but I managed to get the system working fine.  I'm thinking I would not have had any of this fun if I had done a fresh install of 7.10 after I had backup my data (which I would do anyway).  I might try building the system from scratch from the LIveCD when the next release arrives.

Bottom line.  Upgrading to Gutsy was well worth it.  The 3D desktop is fun, there are a lot of improvements in the base system and applications that I keep noticing as I use them.  Good job!

---

