---
title: "Upgrade error: type 'echo' not known"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by DManX04 on 2008-10-27
This is what my upgrade manager tells me when I try to install updates.

-------------------
'E:Type 'echo' is not known on line 58 in source list /etc/apt/sources.list, E:The list of sources could not be read.'
-------------------

Any ideas how to fix this? I'd like to upgrade to 8.10 since I've heard there are fewer wireless problems, but I can't until I get this resolved.

---

### Post by Pumalite on 2008-10-27
Edit your sources.list
gksudo gedit /etc/apt/sources.list
Comment out (put a # in front) the offending line.
Save, exit.
Now sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by DManX04 on 2008-10-27
Thanks man. I've been having this error for about two weeks, but just got around to fixing it. I ended up having to do that for about 5-10 other lines. Any idea how that happened? Also, after I finished that and ran the updater I had about 90 updates, most of which looked like programs I already have. Does that sound normal?

---

### Post by Pumalite on 2008-10-27
It's normal to have upgrades to programs you already have.

---

### Post by DManX04 on 2008-11-01
Ok, I tried to install the medibuntu repository, and now I'm getting a similar error. I'm using Kubuntu only now, and the earlier method that worked in gnome won't work now. I can't even open that file and just edit it normally. It keeps telling me I don't have write permission for it.

---

### Post by Pumalite on 2008-11-01
sudo chmod 777 /etc/apt/sources.list

---

