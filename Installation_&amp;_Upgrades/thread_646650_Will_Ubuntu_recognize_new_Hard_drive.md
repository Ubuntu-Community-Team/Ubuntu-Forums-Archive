---
title: "Will Ubuntu recognize new Hard drive?"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by gander on 2007-12-21
I'm going to install a new hard drive in my computer just for Ubuntu.  The original drive contains Vista.
Will Ubuntu recognize this empty drive at installation and use it.  I've done this before on other
computers using Suse and it worked.

Thank You ....gander

---

### Post by Jadd on 2007-12-21
Should do.
If you have trouble, remember you can always use gparted (System, Adminitration, (GNOME) Partition Editor) from the Ubuntu live CD.
I don't recommend installing on an external drive though.

---

### Post by logos34 on 2007-12-21
> **Jadd said:**
> I don't recommend installing on an external drive though.

Why not?

---

### Post by ugm6hr on 2007-12-21
> **gander said:**
> 
Will Ubuntu recognize this empty drive at installation and use it.  I've done this before on other
computers using Suse and it worked.


As long as you tell it to use that hard drive.  It should do.

To be sure - might be safer to prepartition and format the HD and choose the "Manual" install option to specify your "/" and "swap" partitions.  That way there is no risk of accidentally telling Ubuntu to use the whole drive, and finding that you chose the whole Vista drive!

---

