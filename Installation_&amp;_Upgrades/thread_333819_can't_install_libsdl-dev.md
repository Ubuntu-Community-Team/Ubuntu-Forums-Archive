---
title: "can't install libsdl-dev"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by r.stiltskin on 2007-01-08
I can't install luvcview: when I try to run its makefile, the result is ```
luvcview.c:32:21: error: SDL/SDL.h: No such file or directory
luvcview.c:33:28: error: SDL/SDL_thread.h: No such file or directory
luvcview.c:34:27: error: SDL/SDL_audio.h: No such file or directory
luvcview.c:35:27: error: SDL/SDL_timer.h: No such file or directory
luvcview.c:44:22: error: X11/Xlib.h: No such file or directory
luvcview.c:45:27: error: SDL/SDL_syswm.h: No such file or directory
```and so on...

It seems I need libsdl-dev.
apt-cache search lists libsdl1.2-dev but when I try to install it:```
The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libartsc0-dev but it is not going to be installed
```
If I try to install libartsc0-dev:```
The following packages have unmet dependencies:
  libartsc0-dev: Depends: libglib2.0-dev but it is not going to be installed
```
If I try to install libglib2.0-dev:```
The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is to be installed
```
Actually, libglib2.0.0 (=2.10.3-0ubuntu1) *is* installed, but when I ask Adept to uninstall it, it wants to uninstall 198 packages, so that doesn't seem to be a reasonable option.

Is there a way out of this?

---

### Post by po0f on 2007-01-08
r.stiltskin,

You mentioned Adept so I'm assuiming this is Kubuntu.  Does it have aptitude by default?  Open up Konsole and try installing it through aptitude instead:
```
[FONT="Courier New"]$ sudo aptitude update && sudo aptitude install libsdl1.2-dev[/FONT]
```

---

### Post by r.stiltskin on 2007-01-08
Actually I was using apt-get install...
I had already run apt-get update.

I only used Adept to see what would happen if I uninstalled libglib2.0.0 (hoping that I could then install a different version).

At your suggestion I tried aptitude install libsdl1.2-dev with this result (omitting the uninteresting stuff):
```
...
The following packages are BROKEN:
  libglib2.0-dev
...
...
The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libglib2.0-dev [2.10.3-0ubuntu1 (dapper-updates)]

Score is 20

Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libglib2.0-0 [2.10.3-0ubuntu1 (dapper-updates, now) -> 2.10.2-1ubuntu3 (dapper,
dapper)]

Score is -40

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```

As you can see, I cautiously answered "n" to the first question, and "q" to the second.

Is it safe to simply answer "y"?  Will it automatically downgrade libglib2.0-0?  Without breaking anything?

---

### Post by r.stiltskin on 2007-01-08
Oh well, I took a chance & accepted the 2nd option ("downgrade libglib2.0-0") and it seems to have gone well.

So thanks poOf for the aptitude suggestion.

After that, I was able to successfully compile luvcview.

Unfortunately it doesn't work -- but that's another story...:???:

---

### Post by po0f on 2007-01-08
r.stiltskin,

I'm sorry it didn't quite work out for you.

Side note: I find that using aptitude alone (no Synaptic/apt-get for me) resolves dependencies nicely.  I've never run into an issue such as your's using aptitude.

---

### Post by r.stiltskin on 2007-01-08
poOf:
Don't apologize.  *I'm* sorry if I gave the wrong impression.  Your suggestion was right on target for solving my dependency problem & as far as I can tell nothing was damaged in the process.

When I wrote "doesn't work" I was referring just to luvcview itself -- & it turns out I was wrong.  It is working.  Only the first time I tried loading it, it crashed.  It appears that it was trying to run with "fbcon" as its video driver, maybe because I had plugged in the videocam before installing the linux-uvc driver.  Now it's working, & shows "x11" as the video driver (not sure why it says x11 & not uvc).

Thanks again for recommending aptitude.  It seems much more powerful than apt-get.  In fact, after seeing what aptitude does I wonder why new users are generally steered towards apt-get.

---

### Post by po0f on 2007-01-09
r.stiltskin,

When I said I was sorry about it not working out for you, I meant getting luvcview working.  Obviously, that issue has been resolved as well.  Glad you *finally* got it all sorted out.  :)

---

