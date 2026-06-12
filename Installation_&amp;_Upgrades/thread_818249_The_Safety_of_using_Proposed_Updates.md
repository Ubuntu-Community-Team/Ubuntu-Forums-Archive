---
title: "The Safety of using Proposed Updates"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by SynapseR on 2008-06-04
Hi All,

I have a simple question. (or maybe not..)
Is it "safe" to use the pre-release, proposed updates when updating Heron ?
The main reason is my problem here :

[http://ubuntuforums.org/showthread.php?p=5113070#post5113070](http://ubuntuforums.org/showthread.php?p=5113070#post5113070)

The other is the huge variety of updated programs available.

Would I "break" my system ?

---

### Post by IgnorantGuru on 2008-06-04
Updates do break things occasionally, though not usually the entire system.

My recommendation is to backup your Ubuntu partition before making changes.  It takes just a few minutes and gives you the option to restore it from backup if you don't like the result.
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

---

### Post by Bubba64 on 2008-06-05
I have never had a problem, but I have older computers using generic drivers and very few 3rd party extras just the basic, as of now Hardy.

---

### Post by tgalati4 on 2008-06-05
The linux mint folks got it right with Mint Update.  It hides xserver and kernel updates from the user (by default) as those two updates can cause the most problems for users.  Applications updates normally improve functionality of specific applications while not breaking the rest of the system.  Some expections are some media players which can mess up the playback codecs or streaming frameworks.

So as a general rule, apply all updates but hold off on xserver (xorg) and kernel updates for a few days to see if there is massive breakage as reported in the forums.

On my old Dapper machines, I have applied hundreds of updates simultaneously without problems.  However, the uptime on those machines is 6 to 9 months so the updates build up over time.  I also only apply updates during down time (such as after a power outage shutdown).  Then if there are problems, I can troubleshoot them all at once by doing multiple forum searches.  You can apply several fixes simultaneously and this minimizes reboots and downtime.

---

### Post by Bubba64 on 2008-06-05
Personally I wouldn't use the forums as a indicator of problems except in a specificity of your set up. The forums are where you go for answers to problems and if looked at from the analysis of trouble I doubt any one would use any Linux set up.

---

