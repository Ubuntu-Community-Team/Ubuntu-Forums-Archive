---
title: "Compiz crash in 12.04 - can't get it back"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by dan1701a on 2012-05-05
I apologize if this has already been posted, but I can't find it in the forums, so here goes:

Yesterday I upgraded from 11.10 to 12.04. When the upgrade process finished and the computer rebooted, Compiz crashed. Clicking the button to relaunch Compiz resulted in another crash. The other button essentially told Compiz to stay crashed, but now I have no desktop environment at all. No window borders or controls, and typing in the Keyring password field produces absolutely nothing - the keyboard apparently doesn't function, either. I can get into the control panel by right-clicking on the desktop and clicking "change display" (or something along those lines - I'm in Windows Vista right now), but nothing seemed to work. Rebooting changed nothing. I may have to downgrade back to 11.10 until something is resolved. Any help would be appreciated. TIA.

---

### Post by tvdkolk on 2012-05-05
Same problem here: 

An error message saying that "Compiz" (whatever that may be) has crashed and now the computer doesn't respond to keyboard anymore. Mouse seems to work fine. 
The window manager seems to have issues too: windows don't have a title bar and the Ubuntu menu bar on top isn't visible.

Anyone?

---

### Post by Tanker Bob on 2012-05-05
If you have an nVidia graphics card, this is a known issue with the nVidia 295.40 drivers in 12.04. Please search the forum or the Internet for how to solve the issue.

---

### Post by PauricTheLodger on 2012-05-05
I'm in the same boat. Compiz just crashed, taking Unity with it and doesn't return on reboot. I don't have an nvidia card.

Keyboard and mouse still work fine. I had Thunderbird set up to run on startup so using that to open Firefox =)

Tried following instructions found at [http://askubuntu.com/a/127849]("http://askubuntu.com/a/127849") but nothing happened. I did however get the printout:
```

compiz (core)- Warn: unhandled ConfigureNotify on 0x22000a4!
compiz (core)- Warn: this should never happen. you should probably file a bug.

```

---

### Post by Tanker Bob on 2012-05-05
I also found some instability in compiz when I tried to change a number of its settings with Unity active. I had to disable Unity, make my changes to compiz in ccsm, then reenable Unity when I was done. It's been stable since then. As insurance, I created a terminal shortcut on the desktop in case ccsm crashed while Unity was disabled.

---

### Post by JRV on 2012-05-05
Open a terminal and try:```
sudo dpkg --configure compiz
```

Or maybe the problem is in Unity:```
sudo dpkg --configure unity
```

---

### Post by PauricTheLodger on 2012-05-05
So I used that idea to get a terminal on desktop (cheers btw!)
```
cp /usr/share/applications/gnome-terminal.desktop ~/Desktop
```
and then chmod to fix permissions.

Tried 'unity --reset' again to get the following:
```
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1a00004
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1c000b8
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2800c99
Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing session options...done
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
compiz (core) - Warn: unhandled ConfigureNotify on 0x2e00090!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2e00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2e00093!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2e00096!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x2e00096!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
```

And now alt-tab is also gone =/

---

### Post by JRV on 2012-05-05
If you unchecked the Unity plugin in ccsm you should not have.  Run ccsm and recheck it.

---

### Post by Tanker Bob on 2012-05-05
Yeah, I never got the unity --reset thing to do anything useful. But your output looks like compiz isn't running or partially crashed. Try running ccsm, disable Unity in ccsm, then make your setting in ccsm, then reenable Unity in ccsm, all without exiting ccsm. You may have to logout then log back in to get compiz to run before doing this, though.

---

### Post by PauricTheLodger on 2012-05-05
Cheers JRV and Tanker Bob, something definitely worked anyway!

Switched over to Gnome Classic, ran ccsm, twiddled with Unity enabling and switched to Unity 2d then 3d to see what would happen.

2d moved rapid and 3d was quite slow to get going.

Will update here if anything else happens =)

---

### Post by Tanker Bob on 2012-05-05
I'm sure that you already tried to reinstall compiz, but if not, that's worth a try.

---

### Post by dan1701a on 2012-05-06
Well, now I can't get it to do anything. No key combinations are recognized (since the keyboard itself doesn't appear to be recognized after the Compiz crash) and right-clicking on the desktop no longer functions.

Looks like I'll have to reinstall 11.10. Good thing this was not my primary computer and I didn't have any important data on it. But I need this to work - if Windows ever goes south on me, I have to have a functioning computer, and Ubuntu is the best option out there. But 12.04 broke basic functionality, and having to reinstall 11.10 (assuming I can find the Live CD) is a real hassle. I'll either wait until the stable version (and shouldn't this have been stable before release?) or stick with an outdated version, which is unacceptable.

To paraphrase the guy in the Scott's fertilizer radio commercials, "Fix your OS. Fix it!"

---

### Post by hildon on 2012-05-06
the problem is the unity plugin on your compiz is crashing or maybe unchecked. just take a look to your compiz config setting manager then check the ubuntu unity. ):P

---

### Post by dan1701a on 2012-05-06
Let me reiterate. Nothing works. I can't get to anything. Even recovery mode doesn't work properly. And I can't go back to a previous kernel because the same thing happens.

At this point a reinstall of 11.10 seems to be the best option for me, because I can't spend a lot of time messing around with it. But if there's a command line workaround from GRUB that I can try, I'm appreciative and open to suggestions.

---

### Post by Tanker Bob on 2012-05-06
GRUB doesn't have a real command line. It's a very limited subset. For recoveries, I usually use system rescue CD. I've fix no end of Windoze systems with it, as well as Linux. However, I doubt that it's worth your time at this point. You can retrieve/backup whatever data you wish to save with either a LiveCD or the system rescue CD, but then I'd go back to what was working. You've been at this for two days and it only seems to get worse. Something hosed your system bad. You can try fixing GRUB from sys rescue CD and see if that helps. Beyond that, it's 4th and long - I recommend punting.

---

### Post by dan1701a on 2012-05-06
I'm going to do a couple of things. I can't find my 11.10 live CD, so I'll DL a new one, as well as the 12.04 live CD. I'll install the 12.04 live CD as a fresh install instead of an upgrade and see what happens. If I still have issues I'll go back to 11.10.

I enjoy experimenting as much as the next guy, but my current circumstances don't give me as much time as I'd like, so I just want something to work. It may be a few days (or weeks - urg) but I'll report back on what happens.

---

### Post by Hollonb on 2012-05-12
I had a working version of 11 on my system for a long time.  I upgraded to 12.04 and now I can't get the system to boot due to the Compiz crash on startup.  I switched to Fedora and found that I didn't like the interface as well as Ubuntu so I did a full re-install of 12.04 thinking that would fix it...  I was wrong, the exact same error after a full re-install as I got from the upgrade.  Seeing how many people are getting this error it appears that Ubuntu really jumped the gun releasing 12.04.  I'd like to stay Ubuntu but at this point I'm looking for alternatives.

---

### Post by Tanker Bob on 2012-05-12
Can you run Ubuntu in 2D?

---

