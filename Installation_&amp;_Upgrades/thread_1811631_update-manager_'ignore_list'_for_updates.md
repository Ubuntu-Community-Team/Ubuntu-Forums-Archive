---
title: "update-manager: 'ignore list' for updates?"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by ddastoor on 2011-07-25
Is there a way to block (not talking about removing an entire entry from the software sources list) INDIVIDUAL packages with all it's dependencies from showing up in the update manager ?

I know I can UNCHECK what I don't want to receive updates for, but they will keep showing up when update manager runs. 
Is there like an ignore list file or something that will, going forward stop listing package candidates for updates ?

Just an example: Going forward, i don't want, at all, to receive any updates for, say, haskel and it's dependencies?

---

### Post by jerrrys on 2011-07-26
you can try locking the version.  this can be done with "synaptic package manager", found in the software center.

its under Package>Lock version

---

### Post by ddastoor on 2011-07-28
oh great, thanks... will give it a try...

---

