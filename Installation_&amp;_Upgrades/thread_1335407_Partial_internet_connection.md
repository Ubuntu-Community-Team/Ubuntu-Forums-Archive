---
title: "Partial internet connection"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by chejose on 2009-11-23
I updated from 9.04 to 9.10 and the problem arrived.

I then did a clean install of 9.10 and the same problem.

The net icon says "Auto eth0 active.

I can ping yahoo or google with no problem.

I can use Firefox after setting IVP6 to off.

BUT... Synaptic simply freezes. When attempting to renew Package information it says downloading 15 packages but nothing happens.

When I try the Software Center everything is "not available&#901;. Where can the problem be?

José

---

### Post by lemming465 on 2009-11-24
A couple of things to try:  disable 3rd party repositories, command line updates, and different download mirror / repository.  

For a command line update open Applications --> Accessories --> Terminal and type```
sudo -i
aptitude clean  # may improve things
aptitude update # tries to refresh the package info
aptitude full-upgrade  # tries to download and apply changes
```

If the aptitude update has the same problem as Synaptic (freezes without generating error messages), try a different download mirror.  In System --> Administration --> Software Sources (or Synaptic -> Preferences -> Repositories) on the *Ubuntu Software* tab in the middle of the screen there is a *Download from:* dropdown.  Change it to something else you find plausible.

If that still doesn't fix the problem, and you have any 3rd party repositories enabled, try disabling those (same dialog, other tabs).

---

