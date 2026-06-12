---
title: "Need help creating space to complete Fiesty to Gutsy upgrade"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by jeradams on 2007-11-25
I have been trying to upgrade from Fiesty to Gutsy. While navigting through the process using the Update Manager, I get the following message;

[B]Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 52.4M free space on disk '/boot'. Please free at least an additional 16.4M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.[/B]

My trash is empty, and when I try 'sudo apt-get clean' nothing happens.

How can I free up this space in order to complete the install?

---

### Post by Pumalite on 2007-11-25
How many kernels do you have in Grub?

---

### Post by jeradams on 2007-11-25
kernels? Forgive me for being a beginner, but how do I find that out?

I checked the properties of the grub file and found;

11 items, totaling 155.9 KB

Does this help?

---

### Post by Pumalite on 2007-11-25
Do you see Grub at boot? If you have used Ubuntu for a while, kernels tend to accumulate      
in that list. There you can see how many kernels you have.

---

