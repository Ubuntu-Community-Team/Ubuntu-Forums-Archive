---
title: "Intel Graphics Card Issue"
date: 2015-11-16
forum: Installation &amp; Upgrades
---

### Post by april7 on 2015-11-16
Just loaded Ubuntu 15.04 onto a laptop with intel 852GM/855GM graphics card.  For some reason, the proper driver is not being loaded (in my best judgement).  The problem is precisely similar to the issue in this thread:

[http://ubuntuforums.org/showthread.php?t=1729761&highlight=Intel+82852%2F855GM](http://ubuntuforums.org/showthread.php?t=1729761&highlight=Intel+82852%2F855GM)

except of course for the distro version.  I attempted the fix suggested, but ran into an error when I tried to add to the repositories.  Question is, is this still appropriate?  If so, can somebody please tweak the commands to make it work for me?

---

### Post by deadflowr on 2015-11-17
> [COLOR=#000000]Question is, is this still appropriate? [/COLOR]

Most likely not.
Card is old, perhaps too old to run Ubuntu -proper.

What driver is actually loaded.
Post the output of
```
sudo lshw -c display
```

---

### Post by ajgreeny on 2015-11-17
You will probably need to use a different DE, for example Xubuntu which uses XFCE or Lubuntu (LXDE), both of which are a lot lighter than unity in Ubuntu, which requires a good 3D graphic card to work at properly.

---

### Post by april7 on 2015-11-21
Thank you for your help - Lubuntu is working now!

---

