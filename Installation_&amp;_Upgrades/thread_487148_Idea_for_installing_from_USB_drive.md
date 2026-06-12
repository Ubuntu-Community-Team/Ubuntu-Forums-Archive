---
title: "Idea for installing from USB drive"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by sheol on 2007-06-28
I was thinking of an easier way to install ubuntu from a USB drive.  I thought of the following:

1. Partition the hard drive however you desire.
2. Install Damn Small Linux from a USB installer.
3. Edit the repositories so that they include the desired Ubuntu repos
4. apt-get dist-upgrade

Will this work?  Or why wont this work?

---

### Post by jbennet on 2007-06-28
it wont work. even although DSL is based on debian you cant mix and match debian and ubuntu APT repositories as ubuntus pakages are quirky. I know this as i tried turn my Dapper install into a debian etch system, killing it

---

### Post by sheol on 2007-06-28
Okay, however what if you completely replace the dsl /etc/apt/sources.list with the ubuntu /etc/apt/sources.list 
Then 
apt-get update
apt-get dist-upgrade

?

That way we aren't mixing, we're replacing.

---

