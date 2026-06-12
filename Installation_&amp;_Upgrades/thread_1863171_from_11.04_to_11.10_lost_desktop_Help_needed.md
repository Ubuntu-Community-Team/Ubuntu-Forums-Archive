---
title: "from 11.04 to 11.10 lost desktop Help needed"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by BHEJU on 2011-10-17
Hi
Yesterday I upgraded my EliteBook (with on board Intel graphics).
It's 64 bit system. And I upgraded from built in update manager.
After upgrade and reboot, the system was fine.
THEN, I ran a command (sudo apt-get remove indicator-messages)to get rid of the mail notifier. And after reboot, I lost my desktop env. I don't have access to the panel on left. Nothing in tray / notification area. I only have "file" menu on the top panel. from where I can access my file system.

What do I need to do to get my desktop env back. 
Oh, I even lost the wallpaper I set-up.

Any help is appreciated. 

Thanks,

---

### Post by BHEJU on 2011-10-18
Bump.
I did clean install (format the upgrade) And still have same issue.

Help.

---

### Post by rvguest on 2011-10-21
I have the same problem, but did not update the desktop manager.  I changed display drivers, and modified some preferences.

I logged into the guest account, and all was back to normal for about 15 minutes, then allez-op! the screen went solid color, the top bar went white, the side bar went away, and a minimal menu showed up in the top bar:  "File|Edit|View|Bookmarks|Help".  Under "File": "New Window|Create New Folder|Create New Document||Connect to Server..."

I'm not sure what I changed that did this, but if anyone knows how to reset the environment to default, that would be a great help!

Since the behavior persisted across a re-install, the config files must have been affected.

Any thoughts?

---

### Post by Xanthomryr on 2011-10-21
Same problem here.

The upgrade from 11.04 to 11.10 performed wihout any problems, then some days later I installed some updates and rebooted - bang desktop gone.

---

### Post by Xanthomryr on 2011-10-22
Bump

/edit: This fixed it for me: [http://ubuntuforums.org/showthread.php?t=1866066](http://ubuntuforums.org/showthread.php?t=1866066)

---

### Post by BHEJU on 2011-10-24
This one worked for me...

[http://ubuntuforums.org/showthread.php?t=1863905](http://ubuntuforums.org/showthread.php?t=1863905)

---

