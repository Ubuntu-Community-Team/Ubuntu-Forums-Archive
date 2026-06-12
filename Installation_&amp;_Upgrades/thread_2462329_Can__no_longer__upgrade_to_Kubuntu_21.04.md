---
title: "Can _no_longer_ upgrade to Kubuntu 21.04"
date: 2021-05-18
forum: Installation &amp; Upgrades
---

### Post by kmal42 on 2021-05-18
Hi all,

last week, when 21.04 became available, I upgraded three systems from Kubuntu 20.10 to 21.04 (mostly ok, for some reason, one of the system can no longer display 4K, but that's a different story). This was done on May 12th and 13th.

On Saturday the 15th, I wanted to update a fourth system. Unfortunately, "do-release-upgrade" suddenly tells me that no upgrade would be available ("no new release found."). During the period where the boot loader problem occurred and the upgrade was withheld, I somewhere read to watch the file [http://changelogs.ubuntu.com/meta-release](http://changelogs.ubuntu.com/meta-release) to see whether 21.04 alias Hirsute Hippo would appear there. I did this and indeed last week it appeared there. This caused me to retry "do-release-upgrade" and to update my systems. However, Hirsute Hippo no longer appears in this file, and the file was obviously edited on Friday 14th at 19:52.

I tried to find any announcement about this withdrawal, but could not find anything. Does anyone of you knows what's going on here? I cannot believe that I am the only one with this problem.

Thanks in advance.

Klaus

---

### Post by fizyk on 2021-05-19
Happened to me on all clean Ubuntu systems as well. Wanted to update on Saturday, after postponing the message on 12th, and the hirsute update is not available for any of my systems.

---

### Post by philhughes on 2021-05-19
Been seeing the same on Ubuntu. All I could find was that there seems to be another possible critical shim bug, so they may have suspended upgrades again.

[https://bugs.launchpad.net/ubuntu/+source/shim/+bug/1928434](https://bugs.launchpad.net/ubuntu/+source/shim/+bug/1928434)

---

### Post by kmal42 on 2021-05-19
Hi philhughes[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=546598"),

this makes sense, at least from the dates this bug could match. It was filed and triaged on Friday. Maybe they pulled the ripcord. Thanks for pointing us to it.

Klaus

---

### Post by philhughes on 2021-05-23
Upgrades are indeed suspended due to the shim bug and other issues being watched:

[https://askubuntu.com/questions/1338429/ubuntu-21-04-update-available-then-disappears](https://askubuntu.com/questions/1338429/ubuntu-21-04-update-available-then-disappears)

---

