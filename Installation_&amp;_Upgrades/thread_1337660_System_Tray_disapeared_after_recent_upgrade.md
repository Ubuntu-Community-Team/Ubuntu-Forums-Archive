---
title: "System Tray disapeared after recent upgrade"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by lieberb on 2009-11-25
I'm on Ubuntu 9.10, and all up to date on my upgrades. On Monday, I upgraded and it required a reboot. After rebooting, my system tray was gone (nm-applet, power-manager, volume-control, etc). I'm able to start nm-applet from the terminal and networking then works fine. I could just add each of these back to the startup, but am wondering if theres a better way that will make sure that everything that should be in there, is.

Thanks for any help! 

-Ben

---

### Post by neilg4rqn on 2009-11-28
Sadly I can't offer any help. I just wanted to add that my system when asked to shut-down (Ctrl+Shift+Delete) says that "Panel not responding" and do I really want to shut down.
PS. How do I get a terminal to run from say a 'Launcher' ? just to get by on for now.

HELP Now both top and bottom panels are blank!

---

### Post by Ginsu543 on 2009-11-29
@ lieberb:
If you mean by "system tray" the notification area, have you tried adding it back to your gnome panel? Go up to the top panel and right click. You'll see the menu item "Add to panel..." If you click on that, it will give you a list of items you can add to the panel, including "Notification Area." That should get you your "system tray" back.

@neilg4rqn:
You can add back whatever item you'd like to both your panels by following the method I outlined above for lieberb.

---

### Post by neilg4rqn on 2009-11-29
I would but when I 'right-click' on the top panel at any point nothing happens. Clicking on 'Applications', 'Places' or 'System' does nothing either. I did find the following

Quote from [https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/335662](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/335662)
[I]The bug did not go away for me either, but I noticed that in the Startup menu, the command line is this:
sh -c "sleep 15; exec hp-systray"
I changed 15 to 45, and ever since no error message at startup. I am just a regular user, so just gave it a try, but maybe somebody knows, whether it is an option that delays startup somewhat, and this way Hplip does not want to climb onto the system tray "too early".[/I]

But where is the file mentioned so that I can try this?
Thanks
Neil

---

### Post by neilg4rqn on 2009-11-30
Hi, after a lot of digging I have got my panel back, perhaps I have been confused between panel and system tray but never mind. The answer is on the forum - follow this link 
[http://ubuntuforums.org/showthread.php?t=983507&highlight=panel](http://ubuntuforums.org/showthread.php?t=983507&highlight=panel)
That did the trick for me.
Seasons greetings all
Neil

---

### Post by lieberb on 2009-12-08
Actually, upon further review, it seems none of my startup apps are starting with the system. I'll go ahead and start a new thread since this is a different issue than I had originally described.

Thanks,

-Ben

---

