---
title: "Update problem"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by AlexBryan on 2006-06-11
Hi,
I have a new install of Kubuntu Dapper on a laptop. I've plugged in a network cable and can get the internet (i'm typing this on it now) but none of the apt-get commands work. When I type 'sudo apt-get update' it just says 
'Reading package lists... Done'. 
Apept won't find any new updates, and other commands like 'sudo apt-get install synaptic' dont work either:
Reading Package lists... Done
Building dependancy tree... Done
Pageage synaptic is not availible, but is refereed to by another package.
This my mean the package is mising, has been obsoleted, or is only availible from another source
E: Package synaptic has no installation candidate

What am I doing wrong?

---

### Post by Ivan Matveich on 2006-06-11
You might inspect the file /etc/apt/sources.list. Mine contains (for example)

```

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

```

---

