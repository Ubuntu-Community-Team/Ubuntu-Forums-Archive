---
title: "Apt-get cache"
date: 2005-02-28
forum: Installation &amp; Upgrades
---

### Post by Rink on 2005-02-28
Hi,

Whenever you use synaptic or apt-get to install software from the web, the .deb files are stored locally in your /etc/apt/cache/ (from memory!).

If I want to scrub my installation, can I retain those files so that I don't have to download them again?

Will synaptic go to the local cache and use that rather than universe, etc?

many thanks,

---

### Post by az on 2005-02-28
Yes, you may save them.

Yes, it will use them first, as long as they are the latest versions.  If the packages have been updated, then it will go and get the newest packages.

---

### Post by bored2k on 2005-02-28
Downloaded .deb files are located usually in /var/cache/apt/archives/ i believe .

so u can copy them [backup] and tweak away 
u can even make a repository disc for future use .

---

### Post by Rink on 2005-03-01
[QUOTE=bored2k]Downloaded .deb files are located usually in /var/cache/apt/archives/ i believe .

so u can copy them [backup] and tweak away 
u can even make a repository disc for future use .[/QUOTE]

Yes, I was at work with an XP (spit!) machine when I typed that.

It's good to know that you can make a repository disk there.

I don't have much in the way of band width.

Dave

---

