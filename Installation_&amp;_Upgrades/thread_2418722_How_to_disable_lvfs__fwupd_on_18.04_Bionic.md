---
title: "How to disable lvfs / fwupd on 18.04 Bionic"
date: 2019-05-10
forum: Installation &amp; Upgrades
---

### Post by mobile-harvey on 2019-05-10
Hi

I have set-up a family member with Ubuntu 18.04 to whom I provide remote support via VNC. I am happy for them to install software updates themselves, but I wish to disable firmware updates so that I can install them only when I am physically present.

Today they have received a BIOS update notification via Gnome Software, which I cannot figure out how to disable. Googling hasn't helped much either. So does anyone know, for 18.04, how to stop Gnome Software from automatically checking for lvfs BIOS updates?

One observation is that with Fedora, Gnome Software has an option to view repositories in which LVFS is listed and can be disabled. On Ubuntu 18.04 Gnome Software redirects to the Software & Updates tool to manage the repos, and I'm unable to find any reference to lvfs there.

Thanks in advance for any ideas.
Nick

---

### Post by dino99 on 2019-05-10
I have myself purged gnome software, to get rid of such notifications and or snap proposal. Still using synaptic and prefer it.

---

### Post by mobile-harvey on 2019-05-10
That would work!

I've actually figured it out myself. Here's my cheat sheet notes on how I plan to manage this:

Disable firmware updates:
--------------------------------
sudo apt-get purge fwupd
Check that firmware update prompt is gone from Gnome Software

Re-enable to allow BIOS update:
-------------------------------------
sudo apt-get install fwupd
Then check for updates in Gnome Software and install firmware

---

