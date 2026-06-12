---
title: "Edgy 6.10 boot hangs: considering reinstall"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by i8bugs on 2007-03-26
OK I'm not panicking...we've solved big problems before.  This one is really different though.  I searched the forum for 2 hours and cannot find a similar situation, so I'm starting a new thread.  

I'm using the Mint 6.10 install disk as a live CD right now.

I leave my computer on for days sometimes weeks without a reboot.  Don't know what may have caused this incident but my instincts tell me it was the last update that had all the language packs to it (like 91 packages).  I say that because the install lagged then hung.  I had a hard time canceling it, then I did a reinstall of that update and it seemed to go fine.

Here's the symptoms: The Ubuntu boot graphic (orange bar) completes it boot, then the screen goes black and all I have is a command prompt, no text, just a cursor.  Right after that I notice the A: drive still does a disk check, then total lockup.

When I was a Xandros user, I would put the install disk in, choose install, and it would find my home drive and say "Xandros has found a linux home drive, do you want to use this as your default home drive?" and I would choose yes, get a clean OS, and everything would be back to normal.  If I can do that with Ubuntu, let me know the process...and please draw me a picture cause I'm dense.  I'm willing to do a bit of terminal command hacking to save this thing, cause I have a lot of pictures.
Thanks
i8bugs

---

### Post by zvacet on 2007-03-26
ctrl+alt+F1 
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by i8bugs on 2007-03-26
Thanks, I'll try that now...BBL
i8bugs

---

### Post by i8bugs on 2007-03-26
Did the xserver-xorg, went thru a multiple question test, rebooted, and I'm at the same situation...no changes.

Ready for another suggestion.
bugs

---

### Post by i8bugs on 2007-03-26
Sorry, that didn't work.  I'm looking for more suggestions.
bugs

---

