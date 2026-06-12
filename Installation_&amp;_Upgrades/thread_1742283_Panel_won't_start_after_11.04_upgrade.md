---
title: "Panel won't start after 11.04 upgrade"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by kkinder on 2011-04-28
After upgrading from 10.10 to 11.04, it appears gnome-panel won't start when I login in classic, classic with no compiz, or even failsafe/safe mode. What happens is the login will start, and I'll see an empty wallpaper with a cursor that switches between the hourglass circle spinner and a regular cursor.

If I hit alt+f2, the run dialog will appear, but immediately be killed (or something).

I am able to login with Unity as well as the recovery console. On the recovery console, when I try to launch the panel, I see this:

[blah blah blah]
b2b97000-b2ba8000 r-xp 00000000 08:05 2101405    /usr/lib/gio/modules/libgioremote-volume-monitor.sofish: Job 1, “gnome-panel” terminated by signal SIGABRT (Abort)

Any ideas? Since Unity doesn't work with focus-follows-mouse, but still tries to use focus-follows-mouse, I'm actually using IceWM to report this.

---

### Post by coldbluesteel on 2011-04-28
I had the panel at first boot. System locked up as I was trying to figure out how to move the stupid thing to the bottom of the screen where I like it.

Rebooted and the panel and new taskbar are gone. All my desktop folders and items are there, but no way to access any programs....

Any ideas?

---

### Post by kkinder on 2011-04-29
FWIW, blowing away my panel configuration solved my problem. mv ~/.gconf/apps/panel ~/.gconf/apps/panel-backup

---

### Post by inhumanbean on 2011-06-15
Initially I was able to use gnome-panel after the upgrade (from 10.10 to 11.04). However after a routine weekly update it stopped working. Going into classic menu or trying to invoke gnome-panel --replace would cause the system to freeze. 
   I was able to ssh into the system from another machine and run 'top'. This showed gnome-panel process at 100% and compiz memory rising steadily. Ultimately i fixed this issue, by completely removing gnome-panel using:

sudo apt-get purge gnome-panel

and then installing it

sudo apt-get install gnome-panel.

After this i am able to get into classic mode, or in my case, run unity and do gnome-panel --replace. This gives me all the short cuts of unity and the widgets convenience of gnome-panel.

---

### Post by cmcanulty on 2011-10-14
that didn't work for me. I can only get panels by typing```
 gnome-panel 
```in terminal and leaving the terminal open!Help.

---

