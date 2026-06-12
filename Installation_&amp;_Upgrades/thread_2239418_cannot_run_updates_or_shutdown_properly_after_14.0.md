---
title: "cannot run updates or shutdown properly after 14.04 upgrade"
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by aleva132 on 2014-08-13
I upgraded monday and since then, any time I try to run muon, it doeshn't bother to ask for my password and just says that the proper authorization wasn't recieved.  I can run them with apt-get in the terminal, but only if kickoff deigns to launch it.  Clicking "shut down" doesn't do anything, no matter how I got to it.  I am quite angry about this.

edit: I forgot to mention, I also no longer have sound (volume setting maxed, nothing comes out).

---

### Post by aleva132 on 2014-08-15
An update: Synaptic does call up the authorization but nothing else does.  The driver seems to be stuck on the legacy nvidia driver (304).  I told it not to confirm a logout in the shutdown settings which may or may not allow me to shutdown properly.  I figure the missing sound is from a missing package but I'll fix that after the *critical* functions are fixed.

---

### Post by aleva132 on 2014-08-16
Everything I tried failed but, today it mysteriously started working again.  I have no idea.
Now to find the sound package.

---

