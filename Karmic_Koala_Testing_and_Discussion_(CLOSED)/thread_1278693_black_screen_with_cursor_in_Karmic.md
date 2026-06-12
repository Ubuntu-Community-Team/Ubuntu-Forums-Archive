---
title: "black screen with cursor in Karmic"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by HolidayQueen on 2009-09-29
Pretty self explanatory. Every time my computer gets a little busy (say, Deluge is checking the integrity of a torrent, whilst i try to launch emesene and open firefox) i'll get a black screen with only the cursor showing. There's nothing i can do except to reboot.

Ive tried disabling power management and screensaver but this has not resolves the issue.

Im running on an intel chipset (p4) with integrated ATI radeo xpress 200. Everything is up to date as i check for updates every day in the hopes of fixing this annoying bug.

Many thanks to anyone who can shed some light on this issue :-)

---

### Post by overdrank on 2009-09-29
Moved to Karmic Koala Testing and Discussion

---

### Post by HolidayQueen on 2009-09-30
I have been able to reproduce this bug.

Every time i am on isohunt.com in firefox and download a torrent, once the dialogue from deluge pops up, the screen goes black. Fortunately the last time i had the mouse hovering on the "Add" button, once i clicked, the screen returned to normal 3 seconds later, and a popup ad (flash) appeared in firefox.

Ive also noticed i can get out of the black screen if i got VLC running in the corner of my screen, all i got to do is double click to go to fullscreen mode, and i get my normal screen back.

Now that i can get out of it, it is possible for me to run a monitor or something to provide some technical info on the problem, if anyone would be kind enough to tell me what to run.

---

### Post by HolidayQueen on 2009-10-01
Hmm, i would have expected some feedback by now, if not at least a few questions.

It's not like this is some little annoying papercut such as gnome panel re-organizing my items for me...

---

### Post by dino99 on 2009-10-01
> **HolidayQueen said:**
> Hmm, i would have expected some feedback by now, if not at least a few questions.

It's not like this is some little annoying papercut such as gnome panel re-organizing my items for me...

That's because Big Brother want to know what you are downloading from isohunt ( some suspect files ?)

Remember that piracy is prohibited. :(

---

### Post by danwood76 on 2009-10-01
Its possible that its a flash issue.
Try disabling flash in firefox and repeating, ISOhunt might be trying to get you to buy big black screens.

I never have any issues downloading torrents from my tracker with deluge.

---

### Post by miegiel on 2009-10-01
> **danwood76 said:**
> ...
ISOhunt might be trying to get you to buy big black screens.
...

:lolflag:

I'm suspecting flash too. **HolidayQueen**, are you running 32 or 64 bit karmic? If it's 64 bit you might find salvation [_here_]("http://ubuntuforums.org/showthread.php?t=1259102")

---

### Post by nowin4me on 2009-10-01
> **danwood76 said:**
> Its possible that its a flash issue.
Try disabling flash in firefox and repeating, ISOhunt might be trying to get you to buy big black screens.

I never have any issues downloading torrents from my tracker with deluge.

Possible? Yes.

But I think it's a driver issue. The few last times I tried to install Kramic alpha 5-6 (I think) I had the same problem. And before install I don't have Flash installed. Unless they included it in there this time?

Going to try and install the latest BETA after my anti-virus scan.:lolflag:

I am using a nVidia GeForce 7600GS AGP.
Has anyone submitted a bug report? (I haven't YET!)

> **HolidayQueen said:**
> i'll get a black screen with only the cursor showing. There's nothing i can do except to reboot.

Im running on an **intel chipset (p4)** with **integrated ATI radeo xpress 200**. Everything is up to date as i check for updates every day in the hopes of fixing this annoying bug.

Maybe it's an Intel P4 issue (Maybe not)? I am also running an Intel P4 but as I said above I have an nVidia GeForce 7600GS AGP on my PC.

* Scratches head*

EDIT: I was booting off a live CD and it was a graphic issue. I was wrong I didn't see any cursor but I did see an error message coming from the monitor it's self not the OS.

So could you please ignore this post. Thanks!

---

### Post by HolidayQueen on 2009-10-02
I dont think it has anything to do with torrent trackers. Or flash for that matter.

I just got the bug three times in a row while running deluge and VLC in the background, then i start up update manager, i get the password prompt, and my screen goes black (rinse, reboot, repeat).

Sometimes just launching nautilus (file explorer) will do it.

Im gonna try doing my stuff without deluge running in the background, if it still occurs, then ill try switching off compiz (btw, is there any way to save my compiz settings should i want to turn it back on without reconfiguring all my animations?)

---

### Post by danwood76 on 2009-10-02
Well both deluge and the update manager run off python.
Its possible it has something to do with that.

I would point more towards compiz and possibly the animations you have enabled. It should save your settings if you just change it in the appearance dialogue.

My ATI X200M I have in my laptop never shows these issues, or is that not the same graphics chipset?

---

### Post by miegiel on 2009-10-02
> **HolidayQueen said:**
> I dont think it has anything to do with torrent trackers. Or flash for that matter.

I just got the bug three times in a row while running deluge and VLC in the background, then i start up update manager, i get the password prompt, and my screen goes black (rinse, reboot, repeat).

Sometimes just launching nautilus (file explorer) will do it.

Im gonna try doing my stuff without deluge running in the background, if it still occurs, then ill try switching off compiz (btw, is there any way to save my compiz settings should i want to turn it back on without reconfiguring all my animations?)

Compiz settings are saved in (hidden directories in) your home dir.
```
~/.config/compiz
~/.gconf/apps/compiz
```
The settings aren't removed when you stop starting compiz automatically or uninstall it (thought you could back them up).

---

### Post by HolidayQueen on 2009-10-04
I just realized that i haven't seen a single window dim in quite some time, it usually occurs once or twice a day as a program becomes temporarily unresponsive. Im starting to wonder if this black screen might be compiz dimming the entire desktop by mistake.

---

### Post by HolidayQueen on 2009-10-04
Confirmed. The fault lies with compiz.

Apart from the black screen thing, another issue i was having was all sorts of interferance/feedback/static on the wallpaper/desktop during video playback in VLC. I switched to X11 video output module and the desktop would return to normal, but the video got choppy. so i switched back to default, turned off compiz, and now, my desktop wallpaper is fine, and the screen doesn't go black when the comp gets busy.

---

