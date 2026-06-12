---
title: "GNOME Panel problem after 6.06 install &amp; 130 updates."
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by ACGilbert on 2006-07-26
Following a fresh install of 6.06LTS from the currently available i386.iso file and the 130 updates following that -- i get the following error:

The panel encountered a problem while loading "OAFIID: GNOME_Panel_TrashApplet".
Delete/Don't Delete.

So far I've selected "Don't Delete".

Not bad for a complete Newbie I guess.
Any idea how to resolve this problem?

Thanks,
Don

P.S.: I hate to start another thread as I'm so new here.
So why aren't the iso's updated instead of making you immediately download 130 updates?

---

### Post by mlind on 2006-07-26
You could try to
```

gconftool-2 --recursive-unset /apps/panel
killall gnome-panel

```

You may need to relogin for changes to take effect.

---

### Post by ACGilbert on 2006-07-26
Thanks mlind,
The first command brought me back to a prompt and I could see behind the terminal window that everything on the desktop went away. Then the second command brought up the original message about Delete/Don't delete the applet.
This time I selected 'Delete'. After rebooting, no message and no Trashcan.
Gotta go -- I'll check back tomorrow.
Thanks again,
Don

---

### Post by mlind on 2006-07-26
Yes, panel are supposed to disappear until panel is restarted. You should run that --recursive-unset for /apps/panel again to restore the defaults (get trashcan back).

---

### Post by ACGilbert on 2006-07-27
Hi mlind,

I tried the commands again. Same result. The second command brings back the desktop and the message about the trashcan.

Also tried just the first command, then did a "sudo init 0" from the terminal window to shut the system down. When I restart -- still the message about the trashcan applet.

The 130 updates included an awful lot of libraries with applets. Maybe some dependency or linkage is broken as the desktop is trying to load the trashcan.

If you or anyone else hasn't any further ideas I guess I'll just leave it alone. I haven't loaded the nVidia 3D drivers yet so I could move on to that project.

Thanks, 
Don

---

### Post by mlind on 2006-07-27
Try reinstalling gnome-applets and gnome-applets-data packages

```

sudo aptitude reinstall gnome-applets gnome-applets-data

```

You can also downgrade or remove those packages using aptitude remove/purge.
If reinstalling doesn't fix this for you, try purging both packages. aptitude
will suggest you to downgrade, but choose solution which will remove both
packages and ubuntu-desktop also. Then use aptitude to install ubuntu-desktop
package back (this will also install both gnome-applets packages back).

---

### Post by ACGilbert on 2006-07-27
I'll give that a try tonight!
Thanks,
Don

---

### Post by ACGilbert on 2006-07-28
mlind,
I removed, then reinstalled gnome-applets & gnome-applets-data.
All is well now.
The version went down a level and now the current version shows up in the updates.
I'll deal with that later.
Thanks again for the support,
Don

---

