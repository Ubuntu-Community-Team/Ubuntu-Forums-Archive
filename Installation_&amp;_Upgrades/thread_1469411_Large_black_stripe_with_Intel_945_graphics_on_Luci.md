---
title: "Large black stripe with Intel 945 graphics on Lucid update"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by davidjxyz on 2010-05-02
After upgrading my Thinkpad T60 with Intel 945GM graphics chip from Karmic to Lucid I had a large black stripe across the bottom of the screen once Gnome had loaded (not on the login screen).

Other symptoms were that running "glxinfo" caused a segfault and switching from None to Normal desktops affects failed to load the 3D driver.

It turned out to be because of some old nvidia drivers floating around on my system from sometime deep in the past. I identified them with:

```
$ dpkg -l *nvidia*
```

Then removed them one-by-one with:

```
$ sudo apt-get remove nvidia-common
```

and similarly for all others installed.

I'm not sure how they came to be installed but according to [this thread]("http://ubuntuforums.org/showthread.php?t=929158") may have been accidentally pulled in due to an old packaging error.

Upon restarting X (ctrl-alt-bkspc if you have that enabled, otherwise log out and back in) all was well once more.

I record this here in case others have a similar issue.

Dave.

---

