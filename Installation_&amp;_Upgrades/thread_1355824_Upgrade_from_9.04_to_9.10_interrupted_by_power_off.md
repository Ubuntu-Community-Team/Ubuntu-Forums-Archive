---
title: "Upgrade from 9.04 to 9.10 interrupted by power off"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by tipiglen on 2009-12-15
Ok!  I left the laptop busy upgrading from 9.04 to Karmic, and when I returned it was dead.  I tried booting and it eventually stalled afterr "checking battery state"

CtrlAltF2 got me a terminal and I went root.  I was advised to run apt-config, and did so.  endless problems with parse errors in /var/lib/dpkg/updates.....

Anyway, I've finally got booted in and the touchpad doesn't work.  I seem to be on the old kernel, and when I use CLI for update-manager it crashes saying I've got a broken package... synaptics  finds and offers to fix package, but 'apply' leads to a fatal error....

meanwhile, I'm writing this in a wubi install, which seems to work fine.

Tempted to simply put a hard link to my old /home directory and re-set my bindings...I might also download a new iso and do a clean install (after saving old /home to external drive)

Very frustrating as karmic works great on my wee asus.

Any ideas before I blow this one away?

Grrrrrr!

---

### Post by audiomick on 2009-12-15
I'd save /home and do a re-install. You never know what might be wrong.
And plug your laptop into the power point next time you update...;)

---

### Post by tipiglen on 2009-12-15
> And plug your laptop into the power point next time you update...  
it's a long story....sticky tape and all...;-)

---

