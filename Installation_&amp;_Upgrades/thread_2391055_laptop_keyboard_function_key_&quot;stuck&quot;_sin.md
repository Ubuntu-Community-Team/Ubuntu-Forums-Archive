---
title: "laptop keyboard function key &quot;stuck&quot; since upgrade to 18.04"
date: 2018-05-05
forum: Installation &amp; Upgrades
---

### Post by ccrs8 on 2018-05-05
I just upgraded my laptop from Xubuntu 17.10 to Xubuntu 18.04.  After the upgrade I attempted to log in and kept on getting an incorrect password authentication error.  I thought I was losing my mind, since I had just used that password multiples times in the previous hour to both log in to the computer and to authorize the upgrade itself.  After some freaking out, I finally realized that it was a problem with the keyboard.  It turns out that since the upgrade, my computer thinks that the function (fn) key on the built-in keyboard is constantly being pressed.  Physically pushing the fn key actually makes the computer think that the fn key has finally been released.  So as long as I keep the fn key physically pressed down, I can type normally.

Obviously I don't think there is anything actually physically wrong with the keyboard, as it has never acted up before, it worked multiple times in the 30 minutes leading up to the upgrade, I used it to authorize the upgrade, and I did NOT spend the hour or so while the upgrade was happening smashing my fists against the keyboard or pouring my coffee all over the keypad.  The far more likely culprit is the upgrade.

Also, a plugged in USB keyboard meant for a desktop that does not have a function key works perfectly.

So...anyone have any ideas?

---

### Post by ccrs8 on 2018-05-05
FYI, I tried the suggestion in this thread as it seemed to be similar to what I'm experiencing, but no luck:
[https://ubuntuforums.org/showthread.php?t=2363499](https://ubuntuforums.org/showthread.php?t=2363499)

---

### Post by ccrs8 on 2018-05-06
OK, I figured this out.  For some reason, since the upgrade, my keyboard numlocks was set to ON at start.  I've never had that before.  Since I don't have a dedicated number pad on my keyboard laptop, the keys that doubled as numbers when either numlocks was on or the function key was pressed were all screwed up.  Anyway, I couldn't figure out any GUI way to disable this behavior, so I just did "sudo apt-get remove numlockx" to solve the problem.

---

