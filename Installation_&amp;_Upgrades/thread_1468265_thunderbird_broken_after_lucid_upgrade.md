---
title: "thunderbird broken after lucid upgrade"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by shochatd on 2010-05-01
Things seemed to be working remarkably well after upgrading, except for one problem: When I try to start thunderbird, I get an error alert saying that it is still running but not responding. After poking around, I found the following: My ~/.thunderbird directory now contains only one file, profiles.ini, containing the following:
----------
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/home/david/.thunderbird/default/xazdwzj7.slt
----------
Obviously, there is no directory named default in .thunderbird. But using the find command I was able to find a directory .thunderbird.upstream which does contain default/xazdwzj7.slt. Now I can think of several ways to try and fix this, e.g. put a symlink to .thunderbird.upstream/default in .thunderbird, but what is the correct solution, and why did things get corrupted like this. What is the purpose of changing .thunderbird to .thunderbird.upstream? I can see from my backups that this did occur during the upgrade.

---

### Post by shochatd on 2010-05-01
I have solved the problem by moving the directory ~/.thunderbird.upstream/default into ~/.thunderbird. After doing that, thunderbird came up, and it was obvious at this point that it was trying to migrate my data to a newer version, 3.0.4 (I had been running 2.0.0.24). Judging by all the activity that could be seen in a status area at the bottom, there was some sort of indexing going on. There are also 6 files now with names ending in .sqlite, which presumably are in support of a more sophisticated search capability. I puzzled for a few minutes over how to get to my actual mail folders, and finally tried clicking on a tab that was erroneously labeled with the name of *one* of my accounts (not the one I wanted to look at), and then I could actually see *all* my accounts. I got various error messages about my password being rejected, but once I managed to type it in, I was able to fetch from my POP server. I still don't understand why it renamed my .thunderbird to .thunderbird.upstream, while continuing to think that my data was still in .thunderbird. I can see how someone could easily conclude, in this situation, that all of his mail folders were lost!

---

