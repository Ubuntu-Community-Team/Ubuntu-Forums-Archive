---
title: "How to pin old version of &quot;Mines&quot;?"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by scruffyeagle on 2013-02-07
Recently, I've become addicted to the game of "Mines". I just love it. Recently, I also installed a v12.04 LTS OS (Xubuntu, w/ Kubuntu added afterward). Making a dive for my favorite game (the only one I play), "Mines", I discovered it had changed for the worse, and it wasn't a matter of being Xubuntu color themes; it was also changed under Kubuntu.

1) The color theme has changed to become low-contrast between untested & tested blocks. I don't like it. It makes it difficult to track the numbers & geometries.

2) The game ALWAYS throws up the board size selection window, when starting a new game. I always use the 30x16 standard board, so this is a continuous nuisance.

3) The game doesn't automatically institute the "Pause" function when the window is minimized now. Instead, it just keeps on incrmenting the game play clock. This is also extra work that shouldn't be necessary. It was great before - why change this for the worse?

Now that I've "dumped" my grievances, laying out my reasons, I need to try to find out if I can "pin" the version to the version that's available under the v10.04 OS, and NOT upgrade to the version being supplied under v12.04.

Reading old posts, I found reference for & read the page at [http://jaqque.sbih.org/kplug/apt-pinning.html]("http://jaqque.sbih.org/kplug/apt-pinning.html"). However, this didn't seem to tell me what I need to know.

Maybe I just need someboday experienced to walk me through this? TIA for any help you can provide.

---

### Post by JRV on 2013-02-07
Download the .deb package from:

[http://www.ubuntuupdates.org/package/core/lucid/main/base/gnomine](http://www.ubuntuupdates.org/package/core/lucid/main/base/gnomine)

Download the 32 or 64 bit package, whichever is correct for your system.

Remove the current version with the command:
```

sudo apt-get remove gnomine

```

Install it with the command:
```

sudo dpkg --install FILENAME

```

Do you have synaptic installed?
If not install it with the command:
```

sudo apt-get install synaptic

```

Run synaptic and search for "gnomine"
Click on it to highlight it.
Click on "Package" and select "Lock Version"

---

### Post by tgalati4 on 2013-02-07
The issue of the window size can be solved with a desktop launcher that runs gnomine with appropriate switches:

In a terminal:

```
man gnomine
gnomine --width=30 --height=16
```

(I just tried these switches and they don't seem to work, so even more regressions!)

There must be a configuration file, but I couldn't find it.  You could probably store some settings there as well.

The pause-while-minimize is a real regression.  It doesn't make any sense to keep the clock running when minimized.  For color themes, it probably better integrates with whatever the current desktop environment is, but you would have to dig into the source code.  Perhaps file a bug against gnotime with your experiences.

JRV's detailed solution is typcial for dealing with any package that you want to run from an earlier version.  This assumes no expected breakage because it is a stand alone game.  Trying to run an earlier version of a major package (like xorg) might break other things in your system.

---

### Post by scruffyeagle on 2013-02-08
> **JRV said:**
> Download the .deb package from:

[http://www.ubuntuupdates.org/package/core/lucid/main/base/gnomine](http://www.ubuntuupdates.org/package/core/lucid/main/base/gnomine)

Download the 32 or 64 bit package, whichever is correct for your system.

Remove the current version with the command:
```

sudo apt-get remove gnomine

```

Install it with the command:
```

sudo dpkg --install FILENAME

```

Do you have synaptic installed?
If not install it with the command:
```

sudo apt-get install synaptic

```

Run synaptic and search for "gnomine"
Click on it to highlight it.
Click on "Package" and select "Lock Version"

Excellent! Thank you!

I should also mention that I see you're using my other favorite saying as a sig line. I, also, tack on "including moderation"!

Coooooool!

---

### Post by scruffyeagle on 2013-02-08
> **tgalati4 said:**
> The issue of the window size can be solved with a desktop launcher that runs gnomine with appropriate switches:

In a terminal:

```
man gnomine
gnomine --width=30 --height=16
```

(I just tried these switches and they don't seem to work, so even more regressions!)

There must be a configuration file, but I couldn't find it.  You could probably store some settings there as well.

The pause-while-minimize is a real regression.  It doesn't make any sense to keep the clock running when minimized.  For color themes, it probably better integrates with whatever the current desktop environment is, but you would have to dig into the source code.  Perhaps file a bug against gnotime with your experiences.

JRV's detailed solution is typcial for dealing with any package that you want to run from an earlier version.  This assumes no expected breakage because it is a stand alone game.  Trying to run an earlier version of a major package (like xorg) might break other things in your system.

Yes, a friend of mine told me that dependencies & libraries could make it impossible to pin w/o problems at an earlier version. Thanks!

---

### Post by scruffyeagle on 2013-02-08
UH-OH!

Checking that page out, I discovered it's not providing the mines game independantly. What's available from that link is bundled into a package w/ many other games. Even changing page to the list of available versions still only provides bundled packages. But, that might not be completely beyond coping with...

My idea is this:

*) Completely remove the current version of mines.

*) Add the Lucid repository into Synaptic in the v12.04 OS.

*) Select the old version, & install it.

*) Lock it.

*) Remove the Lucid repository from the sources list.


Think this would work?

---

### Post by tgalati4 on 2013-02-08
I have done that on another package that I needed an earlier version of.  It works, but again the basic premise is you are mixing old and new packages and that makes your system prone to breakage.  If it works great.  If it breaks, you get to keep the pieces.

This is a meta-mine.  Installing mines might blow up your system.

---

### Post by badhat on 2013-02-08
Your package maanger, or the "apt-cache depends" command, can show you the dependencies. Example below, checking kmines on my system (Debian squeeze). You can see it turns out kmines depends on some important shared libraries: c, qt and kde core libs. If I tried to downgrade it, I would probably have to downgrade those libs in the process, which would probably necessitate removing or downgrading other apps that depend on them. If I added an older repo to my sources list, and tried to install the downgraded version, my package manager probably would probably balk, presenting a long list of apps that needed to be removed, to resolve conflicts.

$ apt-cache depends kmines
kmines
  Depends: kdebase-runtime
  Depends: libc6
  Depends: libkdecore5
  Depends: libkdegames5
  Depends: libkdeui5
  Depends: libqt4-svg
  Depends: libqtcore4
  Depends: libqtgui4
  Depends: libstdc++6

---

### Post by scruffyeagle on 2013-02-09
_tgalati4_ & _badhat_:

Thanks for the comments. I'll proceed with great caution.

---

### Post by tgalati4 on 2013-02-09
Sometimes you can simply take the binary and copy it over from another (older) machine.

```
which gnomine
ls -la /usr/games
```

tgalati4@Mint14-Extensa ~ $ which gnomine
/usr/games/gnomine

tgalati4@Mint14-Extensa /usr/games $ ls -la
total 152
drwxr-xr-x  2 root root    4096 Feb  7 10:57 .
drwxr-xr-x 10 root root    4096 Oct 17 07:56 ..
-rwxr-xr-x  1 root root    4421 May 28  2012 cowsay
lrwxrwxrwx  1 root root       6 Dec 28 10:34 cowthink -> cowsay
-rwxr-xr-x  1 root root    1563 Oct  8 05:49 espdiff
-rwxr-xr-x  1 root root   23056 Jul 27  2012 fortune
-rwxr-sr-x  1 root games 107128 Jan 15 03:39 gnomine

Sometimes using the older binary will work if the library calls are generic and not too tied to a specific version.  That way you can keep all of the dependencies current.

---

