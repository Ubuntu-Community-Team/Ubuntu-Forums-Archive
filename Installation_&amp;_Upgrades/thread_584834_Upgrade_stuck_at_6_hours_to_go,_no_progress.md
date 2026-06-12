---
title: "Upgrade stuck at 6 hours to go, no progress"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by t2000kw on 2007-10-21
I'm having problems with the upgrade and need to know if it's OK to reboot and what will happen if I do. 

I thought this would be a painless upgrade but I see the bugs haven't been worked out yet. 

I do have a separate /home partition, so my email and some other stuff is safe, but I may lost my Crossover Office installation (not sure) and I'll have to back up my email (a Windows program) before doing anything radical.

If I reboot will the upgrade continue where it left off?

I would include the "terminal" output if I could but it won't let me copy the contents to the clipboard. 

Donald
----------------------------------------------

---

### Post by dimeotane on 2007-10-21
I had a similar problem with the upgrade process crashing with an hour to go.  I think all the upgrade packages were downloaded however.   Like you I'm happy my /home is in a separate partition in case I needed to redo a fresh install of the system from an install CD.

you may wish to try 
```

sudo aptitude update
sudo aptitude upgrade
sudo aptitude full-upgrade
```

---

### Post by t2000kw on 2007-10-21
I ran sudo apt-get update and got an error message about dpkg, ran the correction for that, and things chugged along until the system froze up completely, including the keyboard and mouse. 

I'm waiting for a friend to steer me through fixing this with chroot. 

Depending on how this goes, I might go to Dapper instead of upgrading from Feisty. Or, just clean house and install Gutsy.

If I would install Gutsy and format my / partition, and uncheck "format" on the /home partition, will Gutsy recognize the /home partition automatically, assuming that I tell it that the /home partition is hda2 (or whatever it is)?

---

