---
title: "Relocate /home"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by Jloser on 2007-06-11
I want to relocate my /home directory to a separate HD.  I want this for several reasons, the HD is giant, and I want to be able to use the same /home/username across several distributions of Linux so I always have access to my same files no matter what distro I am in.  

What is the easiest way to do this?

Where there be any problems because of settings that are stored in these places messing up files from different distros?  Is there a better way to do this?

---

### Post by Ek0nomik on 2007-06-11
Here is a guide to help you with it:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Jloser on 2007-06-11
I saw that, but are there going to be any negative side affects from using the same /home/user across several distros?

---

### Post by kevinlyfellow on 2007-06-11
> **Jloser said:**
> I saw that, but are there going to be any negative side affects from using the same /home/user across several distros?

Potentially there is.  I just do this /home/user_distro and exclude the (_distro) part from my username

---

### Post by Ek0nomik on 2007-06-11
Since /home generally contains some program configurations and other information similar to that, I imagine it won't harm your system, you just may have files being useless from one distribution to the next depending on window environment, etc.

---

### Post by aquavitae on 2007-06-11
If, for example, you're using kde on two systems, they will share configurations.  I.e. themes, menus, etc will be the same.  I have a similar setup, but what I've done is put all my personal stuff onto a separate hd, an mounted it to ~/docs.  That way /home is unique on each system, but I still have access to my personal documents across systems.

---

