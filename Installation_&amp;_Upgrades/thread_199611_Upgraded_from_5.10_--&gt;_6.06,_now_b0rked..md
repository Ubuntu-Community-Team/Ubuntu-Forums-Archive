---
title: "Upgraded from 5.10 --&gt; 6.06, now b0rked."
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by Cheule on 2006-06-19
Hi all, got a big problem here and no clue what's happened to cause it.

Firstly, I was running a perfectly-working 5.10 install for many months, eventually I decided to upgrade and that's where the problems began.

The upgrade seemed to go smoothly, all files/folders created/updated properly. However, on reboot, I get the "X cannot start" problem. Ok, no problem, I'll just sudo dpkg xserver-xorg and run through the prompts, change the graphics driver to vesa and reboot.

Rebooted.

Same thing. Changed the vesa driver to the ati one.

Rebooted.

Same thing. Tried various other options including directly editing the xorg.conf file directly. Nothing helped.

Now it's got even worse, I seem to now be stuck in some kind of loop. What happens now is, upon booting, I get the Ubuntu splash screen inviting me to login, I enter my username and password which are accepted, then after a bit of loading, I'm dumped at the command line where it again asks me to login using my details. Once I do that, a bit of loading ensues and I'm then back at the Ubuntu splash screen, where - you guessed it - it wants me to login!

Only the option on the splash screen which forces use of the command line works, but I've no idea what to do with it now.

Please, can someone help? I'm at a total loss :(

---

### Post by munckfish on 2006-06-19
Hi 

Sorry to here you're having such a weird experience.

Have you checked for any error messages in your /var/log/Xorg.0.log file?

---

