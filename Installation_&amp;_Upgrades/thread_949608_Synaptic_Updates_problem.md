---
title: "Synaptic Updates problem"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by fikelfikel on 2008-10-16
I just went to update ubuntu, and it came up with a list of updates. I selected Install Updates, and this error suddenly came up:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

It dosn't even work in Add/Remove or any Synaptic based updater. I'm running Hardy Heron and this problem is killing me. How do I update?

Oh yeah, if you want to know how I connect my internet, it's through GNOME PPP.

It worked every time before that, so I'm unsure of what to do. Please help!

---

### Post by Pumalite on 2008-10-16
Make sure you have Synaptic and all other instances of apt-get closed
Click on the button or try:
sudo apt-get update
sudo apt-get dist-upgrade

---

