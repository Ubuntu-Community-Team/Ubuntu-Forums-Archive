---
title: "need help installing new GIMP"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by roaddummy on 2008-11-29
I want to install the newer version of GIMP.  It gives me something to type in to update it, but I do not know where to type it in.  This is what I need to type in:

apt-get install gimp

Does anyone know where I need to put this???  Thank you for the help!!

Melanie

---

### Post by oldos2er on 2008-11-29
Applications, Accessories, Terminal. Copy and paste this: sudo apt-get update && sudo apt-get install gimp

---

### Post by CastilleV on 2008-12-03
> **oldos2er said:**
> Applications, Accessories, Terminal. Copy and paste this: sudo apt-get update && sudo apt-get install gimp

I hate to burst your bubble, but that does not work.
Does any one know of a way to make it work?

---

### Post by oldos2er on 2008-12-03
> **CastilleV said:**
> I hate to burst your bubble, but that does not work.
Does any one know of a way to make it work?

 Can you post the output from the command?

---

### Post by cariboo on 2008-12-03
You need  to be root to install programs, the reason your command didn't work is you forgot to add sudo to the command.

Gimp is installed by default and depending on what version of Ubuntu you are running, you may not be able to upgrade.

Have a look here for the various versions:

[http://packages.ubuntu.com/search?keywords=gimp&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=gimp&searchon=names&suite=all&section=all)

Jim

---

