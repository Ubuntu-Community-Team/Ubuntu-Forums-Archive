---
title: "problems with update manager"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by luisrauljimenez on 2007-05-29
hey guys!!
I have problems with my update manager... everytime I try to run it it closes suddenly...
I don't know what's going on... not even an idea... because of that I hadn't be able to upgrade to 6.10 version
plzzz help!!!!

---

### Post by bapoumba on 2007-05-30
hello, what does **update-manager** return (> Accesssories > Terminal) ?
You can still updat/upgrade/dist-upgrade with aptitude or apt-get.
What is the output to:
```
sudo aptitude update
```

---

### Post by luisrauljimenez on 2007-05-30
I tried to run the code in a Terminal but it says that is reading the package lists... after that, it shows me an error message
Then, it says:

E: Dynamic MMap ran out of room
E: Error ocurred while processing pyhton-pgsql (Newversion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edg
y_universe_binary-1386_Packages
E: The package lists or status file could not be parsed or opened.
Reading package lists... "here it starts to load"

Suddenly, it closes... 

:S:S:S:S:S:S help plzz

---

### Post by taurus on 2007-05-30
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by bapoumba on 2007-05-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/debian/+source/apt/+bug/24626](https://bugs.launchpad.net/debian/+source/apt/+bug/24626) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				```
sudo apt-get update -o APT::Cache-Limit=25165824
```
And you should be fine.

---

