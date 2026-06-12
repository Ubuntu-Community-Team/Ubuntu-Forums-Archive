---
title: "Updating"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by cbk1994 on 2007-04-05
This is driving me mad! How do I update Samba? I have no idea where to put this post. Linux seems like the most complicated thing to update with. I download the .gzip file, but now what do I do with it? I already have Samba installed, I just need to update.

Thanks.
Ready to throw this thing out the window ...

---

### Post by mikesignguy on 2007-04-05
why are you not using SAMBA from the repositories??

sudo aptitude update
sudo aptitude upgrade

---

### Post by Zwalther on 2007-04-05
Are you sure you need a newer version of Samba? I would only upgrade if you absolutely need a feature that is in the newest version of Samba and not in the ubuntu package. 
You can install it from a downloaded gzip, but it might give you problems when you want to update ubuntu. Plus you won't get the automatic security updates from ubuntu anymore.

But if you really, really want to update, you should uninstall the ubuntu version of samba and then read the documentation in the .gzip file. You should probably start with docs/htmldocs/Samba3-HOWTO/index.html. That file has a link to the installation procedure.

---

