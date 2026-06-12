---
title: "Standards amendment: Commenting in auto-generated configuration files"
date: 2008-08-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jharr on 2008-08-02
When I upgrade from one release of Ubuntu to the next, a lot of configuration files become machine generated. This is great; not a problem. What is a problem is when the configuration files 1) do not indicate that they have been automatically generated and 2) do not indicate where which service is changing them and where to go to affect this configuration file.

This is happening with /etc/dhcp3/dhclient.conf and /etc/resolv.conf. Now I know that these are now managed by the NetworkManager, but the configuration files do not indicate this. I end up searching google to figure out what is going on, then I'm fine, but I have just wasted 10 minutes figuring out what's going on. New users may not be so quick.

I propose a standard that requires auto-generated files to have these in their comments:
- That this file is auto-generated and will be overwritten.
- Which program made the change.
- Where one should make configuration changes (whether it be a gui application, or another config file).

Maybe I'm too late for this to make it into Intrepid, and I don't expect every package to comply immediately, but having something like this in the standard would better the Ubuntu distribution out over the long run.

---

### Post by ronacc on 2008-08-02
don't you realise that linux is supposed to be arcane and esoteric , what you propose makes sense and we can't allow that .:lolflag:

---

### Post by RamBalaraman on 2008-08-02
Good idea!

Maybe you should also post in [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by klange on 2008-08-02
There are automatically generated configuration files that lack comments?
Why was I not informed of this heresy?

---

### Post by Gina on 2008-08-02
> **rambalaraman said:**
> good idea!

Maybe you should also post in [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)+1

---

### Post by cszikszoy on 2008-08-02
> **RamBalaraman said:**
> Good idea!

Maybe you should also post in [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

Great Idea, perhaps try posting here too?

[http://ubuntuforums.org/forumdisplay.php?f=306](http://ubuntuforums.org/forumdisplay.php?f=306)

That's the Ubuntu Idea Pool forum.

---

### Post by Nullack on 2008-08-02
Yes, good idea

---

