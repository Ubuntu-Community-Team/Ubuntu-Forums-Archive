---
title: "Please help!!! Keyboard on infinite repeat"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by tipiglen on 2010-05-10
I was uograding from a perfectly workable karmic. While unattended the upgrade paused at the grub (keep/discard customised) question, and the whole thing froze.

Had to hard reset to restart, and after considerable trouble can now boot into an apparently working system, 

EXCEPT when using anything requiring keyboard input (password?) the keyboard seems to go into manic repeat mode and the entire system freezes.

I can manage to get a root terminal, but I have no idea what I should do from there.

Any ideas?

In frustration,
ed

---

### Post by Dougie187 on 2010-05-10
Once you get to a root terminal, try this.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by tipiglen on 2010-05-10
> Once you get to a root terminal, try this.
Have done the first two.  Will try the third

Thanks

---

### Post by tipiglen on 2010-05-10
First gives sources list and no comment.
Second and third give 
0 upgraded, 0 newly installed, 0 to remove, and 0 upgraded

So no apparent joy there.  Once more into the reboot breach!

I may be some time....

---

### Post by tipiglen on 2010-05-10
On reboot, touchpad works, but ANY keyboard input (even ctrl/alt/F2) causes freeze.

Tried (via touchpad) to do system/preferences/keyboard/general and alter (seemingly normal) repeat and speed settings.  Set to slowest, longest delay, etc., amnd typed one character in test space =

a string of (albeit slower) characters and a frozen computer

Hard reset!...................

---

### Post by tipiglen on 2010-05-10
Works fine if booted in recovery mode and then low graphics.

Any ideas what to fix?

---

### Post by LSenf on 2010-07-17
Have you found a good solution for the problem?

I did a fresh Lucid install, but I get the same problems.
Using an external keyboard and mouse works fine, the touch pad works till the first key of the built-in keyboard is pressed.
Changing the keyboard layout or model does not help either.

---

### Post by LSenf on 2010-07-25
Got it - for me, the boot option acpi=off solved it.

I posted the complete solution in the following thread:

[http://ubuntuforums.org/showthread.php?t=1538006]("http://ubuntuforums.org/showthread.php?t=1538006")

---

