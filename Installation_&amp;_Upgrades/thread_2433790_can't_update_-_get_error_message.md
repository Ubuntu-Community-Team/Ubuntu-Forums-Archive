---
title: "can't update - get error message"
date: 2019-12-25
forum: Installation &amp; Upgrades
---

### Post by x99 on 2019-12-25
When I try to update I get an error message, when I try to run synaptic package manager it just gives an error report and closes

it says:
E: Unable to parse package file /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_bionic-backports_InRelease (1)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


I do not know enough to know what this means!  Can anyone advise (in step-by-step instructions!) what can I do to fix this?  

(This pc is just used for basic web-browsing and I'm not a linux expert of any kind!)

This is using Lubuntu (can't find where it says a version number)

Thanks.

---

### Post by Bashing-om on 2019-12-25
x99; Hello -

Corrupted data base,likely.

Try:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt update
sudo apt upgrade

```

"MergeLists are a working tool of apt, part of the way it keeps track of which packages are in which repositories. It's the gears of a text-based database that apt relies upon. When corrupted, they can be safely deleted. Apt will recreate them during the next apt update."

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by x99 on 2019-12-25
Thanks v much for the quick (and useful) reply.  That seems to have fixed the problem.

---

### Post by Bashing-om on 2019-12-25
x99; Great !

Pleased was an easy fix.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

