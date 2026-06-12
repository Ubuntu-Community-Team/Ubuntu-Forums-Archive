---
title: "Update Mgr: Section with no package"
date: 2012-12-13
forum: Installation &amp; Upgrades
---

### Post by pschalkx on 2012-12-13
[I]Hi guys,

My machines with Ubuntu 12.04 64 bit woke up today with a red "halt"sign on the update icon, that shows the following message when I run the update manager or run apt-get from a terminal.

I also tried synaptic and it show the same error an then closes

Here's the output:[/I]


Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

[I]Any idea what's wrong?

Tks!

Philip[/I]

---

### Post by ibjsb4 on 2012-12-13
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

should fix it

---

### Post by pschalkx on 2012-12-15
Hi ibjsb4,

I ran your commands and issue is fixed!

This community is just brilliant!

Thanks!

Philip

---

### Post by ibjsb4 on 2012-12-16
Welcome  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

