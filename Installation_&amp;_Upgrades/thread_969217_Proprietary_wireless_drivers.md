---
title: "Proprietary wireless drivers"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by kanonk on 2008-11-03
When I tried to use Ubuntu 8.10 on my laptop it needed proprietary drivers for the wireless network card to work. You can download it within ubuntu, but how am I supposed to do that without internet? I have no wired connection.

---

### Post by DemonWasp on 2008-11-03
8.10 comes with the WL driver pre-installed. If that driver supports your card, you can probably enable your wireless with a few commands and no download required.

Other than that, are you sure you can't get a wired connection? Does your computer simply not have a wired connection, or do you not have access to a drop point? The second one is much easier to solve - just go to a library or similar.

It would also be helpful if we knew what kind of hardware you had. Try posting the results of the following commands:

lspci -nnm  # With this one, try to just post the lines that correspond to your wireless and wired cards
lshw -C network

---

