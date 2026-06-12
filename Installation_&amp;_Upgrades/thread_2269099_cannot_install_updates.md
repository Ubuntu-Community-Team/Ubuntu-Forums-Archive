---
title: "cannot install updates"
date: 2015-03-13
forum: Installation &amp; Upgrades
---

### Post by StuartCarter on 2015-03-13
I get update alerts, but when I try to install them I am not prompted for the superuser password and the update crashes out with 

Authentication error - Muon Update Manager
This operation cannot continue since proper authorization was not provided

I have to drop to a terminal and run sudo muon to be able to install updates. Restarting ufter updates also requires running sudo.

This is a significant impairment to basic functionality of my system. Whoever screwed up the permissions should admit it, apologise, and provide a fix. Running sudo in a terminal is NOT an acceptable way to handle this.

---

### Post by QIII on 2015-03-13
I have encountered so many problems with muon over the years that one of the first things I install is synaptic.

That said...

Installation of software should require elevated privileges, be it muon, synaptic or terminal.  That is expected.

If you are trying to reboot from the terminal, doing so with elevated privileges is also expected.

None of this is "messed up" permissions.  This is by design.

---

### Post by StuartCarter on 2015-03-13
> **QIII said:**
> I have encountered so many problems with muon over the years that one of the first things I install is synaptic.

That said...

Installation of software should require elevated privileges, be it muon, synaptic or terminal.  That is expected.

If you are trying to reboot from the terminal, doing so with elevated privileges is also expected.

None of this is "messed up" permissions.  This is by design.


Muon USED TO Prompt for elevated privileges - "please type your password". It no longer does so. Previously existing permissions were broken.

Updates requiring a reboot prompted for a reboot with a handy little "reboot required" icon which, when clicked, would reboot the computer. The "reboot required" icon now does nothing. Previously existing permissions were broken.

I should not HAVE TO drop to a terminal and escalate permissions in this manner just to carry out basic functionality! I am saying that SOMETHING HAS CHANGED. And that something has broken previously existing permissions.

---

### Post by QIII on 2015-03-13
I would suggest reporting it as a bug, then.

None of us here can do anything about it.

I quit using muon a long time ago because it always seemed that whenever I turned around a new problem cropped up.

---

