---
title: "Could not initialize package information"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by Faizal4in on 2007-12-11
Hi All,

I am getting this error while trying to access synaptic , add/remove programs.
Please help.
I was trying to enable sound in my HP dv 2025 laptop.
But  a simple sound issue has turned into major software problem.
Please help to activate sound


Regards,

faizal

---

### Post by zvacet on 2007-12-11
**system>administration<software sources>chek all in first tab and in updates tab>close.** This will enable  all repositories.Chek your source list.Applications>accessories>terminal

```
gksudo gedit /etc/apt/sources.list
```

If any line look like

#deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse universe

make it look 

deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse universe

This line is jut example.After all lines look like second one save and close file.

```
sudo apt-get update
```

---

