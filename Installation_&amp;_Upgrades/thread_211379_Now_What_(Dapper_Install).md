---
title: "Now What? (Dapper Install)"
date: 2006-07-08
forum: Installation &amp; Upgrades
---

### Post by facefur on 2006-07-08
OK, so last night, I decided to upgrade to Dapper.  After reading the posts here and determining that I would use the auto-update, I selected the "Upgrade" option from the auto-update notifer.  After several tries that resulted in being unable to download any upgrades from the servers, I decided this was not working. (I'm slow, but not hopeless.)

I bit the bullet, and downloaded the "alternative" version, created the ISO image, and ran the CD.  Booting from the CD brought me to the installation menu.  Given the cryptic range of choices, I selected "OEM".  During partitioning, I carefully saved my existing /home and /windows partitions, formatted the rest, and off I went.  I actually let it run overnight, and this morning, it completed.  The Auto-updater ran me through another set of newer stuff, and it's up and running (that's how I'm here).

What I need clarified is:  1.  What's this OEM login thingy and how do I get it to recognize my old logins? (The files are all there).  2.  When I reinstall Thunderbird, can I simply reuse my old account and get my files back without writing a book in the terminal?

---

### Post by Rui Pais on 2006-07-08
> **facefur said:**
> 
What I need clarified is:  1.  What's this OEM login thingy and how do I get it to recognize my old logins? (The files are all there).  2.  When I reinstall Thunderbird, can I simply reuse my old account and get my files back without writing a book in the terminal?

hi,
about OEM i don't know nothing.

about old thunderbird files, check if you have a ~/.thunderbird? if so try to mv it or copy it to ~/.mozilla-thunderbird

---

### Post by PriceChild on 2006-07-08
oem is just used as a standard username for reselling pcs.

You can log in using hte username "oem" and the password your suplied.

I would create your new account, delete oem, and restore your home partition, then re login


Oh and you may wanna be careful about restoring al your home partition. I would only replace your own files, not the config folders. Means that you don't transfer any old errors to the new system.

---

