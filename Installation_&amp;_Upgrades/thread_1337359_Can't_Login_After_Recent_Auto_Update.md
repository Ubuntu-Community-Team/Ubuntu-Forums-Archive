---
title: "Can't Login After Recent Auto Update"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by glicholas on 2009-11-25
Hi all,
      I woke up this morning and was lucky enough to have an auto update ready on Karmic Koala.  After installing it, it asked me to reboot, which I did.  I am now welcomed by the regular login screen.  After I type in my password, the screen flickers a few times, I see some text for half an instant, and then it goes back to the login screen.  Any help would be greatly appreciated, I'm at home for break so I can't access my desktop to make a clean install which is what my lazy butt would regularly do...The problem is on my laptop, dual core intel 2.5ghz.  2gb ram, nvidia 8600 gm.

---

### Post by alwayshere on 2009-11-25
when ya boot push Esc to see more options that should help ya out start in recovery mode and let it do its thing then choose xfix -Try to fix x server (use arrow keys and tab key to chooser options ) that should sort ya out i hope .

---

### Post by glicholas on 2009-11-25
I was able to boot into recovery mode and try the option that "repairs packages" but no luck.  However, I was able to login in with the prompt mode.  Is there a way I can use this to revert to before the update? That is, if there's nothing else to do to fix this for now.

---

### Post by uncledeath on 2009-11-25
Same problem here :(

HP Compaq 6710b with GMA965 chipset

---

### Post by jaylsi on 2009-11-26
I have offered this suggestions 3 times already in a day, but here goes again: :)
1) On login screen, click user name, and enter password, but don't hit enter yet. Select "failsafe gnome" from the session list at bottom of screen, then login.
2) Go to System->Administration->Hardware Drive to install video driver
3) Reboot

Good luck.

---

### Post by uncledeath on 2009-11-26
I can't see any gnome safe mode button in the login screen. In my case sudo apt-get install ubuntu-desktop helped although I don't understand why - it only installed empathy and rhtyhmbox that I removed a few days ago. I hope my solution works for other users too

---

### Post by alwayshere on 2009-11-28
push Esc button while booting  you should see a list the highlighted line at the top is the newest if ya want to roll back just use arrow button to highligt a earlier kernel version not labled as (recovery mode ) note the lower the numbers the older the version.

---

### Post by NeilHoskins on 2009-12-07
I had the same problem, and was going to try some of these fixes this evening.  However, it just booted fine.

Bizarre.

---

