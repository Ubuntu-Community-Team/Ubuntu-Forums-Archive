---
title: "Going from xu9.04 to U10.04, somebody check me"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by pstrbrc on 2010-11-24
Toshiba Satellite
am using a slightly buggy Xubuntu 9.04, want to do a new install of Ubuntu 10.04lts. I stuck with the 9.04xfce environment for this long because it was a real pain to get my Atheros 9004 wifi card to work, and I didn't want to go through that again. But 10.04 seems to use my wifi card right out of the box, so here goes.
I'm planning on putting my entire HOME directory (61gb) on an external hard drive, but I'm concerned about where my Firefox and Thunderbird files are saved. What do I need to do to save bookmarks, passwords, and e-mail folders?

---

### Post by matt_symes on 2010-11-24
Hi

They are all saved in your current home directory in hidden directories.

Open nautilus in you home directory and press 

ctrl h

to view the files. Or open a terminal and type

ls -al

to view them in a terminal. You should just be able to copy them across.

Kind regards

---

### Post by pstrbrc on 2010-11-24
Thanks. I knew I was forgetting something. Once I click "show hidden files" I find them. Thanks!

---

### Post by pricetech on 2010-11-24
If you just want bookmarks and address book, each can be exported and imported in the new install.

I'd probably do that just to back them up anyway, something I do from time to time for that purpose.

---

### Post by pstrbrc on 2010-11-25
Worked sweet. Backed up my home directory on an external harddrive, did a new install, then took what I wanted from the backup. Works perfectly. I'm one happy camper.

---

