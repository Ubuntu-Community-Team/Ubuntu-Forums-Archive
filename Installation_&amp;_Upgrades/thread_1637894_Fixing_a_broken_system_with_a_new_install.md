---
title: "Fixing a broken system with a new install"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by lnoland on 2010-12-05
I had one of my Linux boxes suddenly start failing -- it would go to blackscreen the minute the window manager loaded, and apparently then took a trip to La-La land -- the network connection would sever, sometimes it would reboot, sometimes it would just sit there completely inaccessible.  I don't think the problem was one of configuration because I had made no recent configuration changes (I hadn't even loaded any updates for at least a week).  Whether it was a configuration problem before, it may have one now -- I have been trying everything imaginable to get it working again including adding and removing packages, reinstalling packages, etc.  It still isn't working and I'm ready to throw in the towel -- I am going to reload from scratch.

I am currently on 9.10 so I planned to load 10.10.  I would like to use the trick of saving my home partition, backing up a list of my packages, copying /etc (and perhaps /var and /usr -- I'm never clear on what's best here) and using those to get back my old configurattion.  The problem is, at least some things in my old configuration are not healthy.  Foolishly, I haven't done a backup in a long time so the backup is no help.  Since the problem appears to be with either X-windows or the window manager, I thought perhaps I could selectively restore my configuration, if I can just figure out what to include and what not to include.  Would anyone have any ideas on how to do that?

I thought perhaps, if I were to uninstall with the purge option anything having to do with X or the windowing environment (in this case, XFCE) perhaps that would clean out any configuration problems in the current setup and I could load the new system and do some kind of merge of settings between the old and new.  Does this seem plausible?  Has anyone attempted anything like this?  I just hate to think of how long it took me to get everything set up and configured the first time -- I really don't want to repeat that (I know -- I hsould have done regular backups).

thanks for any help you can offer.

- Les

---

