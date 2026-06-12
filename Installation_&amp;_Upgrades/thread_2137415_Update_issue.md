---
title: "Update issue"
date: 2013-04-20
forum: Installation &amp; Upgrades
---

### Post by ers11121 on 2013-04-20
Unable to use update manager for the last several days, install the last rouns of updates 9 days ago and hasn't worked sinc. Everything else is fine. Ran sudo apt-get update it shows a of lines of packages but nothing updates. Below is the error that comes up:
  * W:Failed to fetch [http://themelinux.com/themes/dists/themes/Release](http://themelinux.com/themes/dists/themes/Release)  Unable to find expected entry 'all/source/Sources' in Release file (Wrong sources.list entry or malformed file)**, W:Failed to fetch [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/source/Sources)  404  Not Found*
*, W:Failed to fetch [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found*
[I], E:Some index files failed to download. They have been ignored, or old ones used instead.

[/I]any suggestions ? This is 12.04

---

### Post by mikewhatever on 2013-04-20
You've added some third party repositories that, apparently, no longer work. Run **gksu software-properties-gtk**, switch to the Other Software tab, and remove those repos.

---

### Post by ers11121 on 2013-04-20
> **mikewhatever said:**
> You've added some third party repositories that, apparently, no longer work. Run **gksu software-properties-gtk**, switch to the Other Software tab, and remove those repos.

That solved it, thank you Mike

---

### Post by claracc on 2013-04-21
> **ers11121 said:**
> That solved it, thank you Mike

Please, mark the thread as solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

