---
title: "General question about Ubuntu pre-releases"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by amauk on 2009-08-14
Hey ho,

I'm a free-lance sysadmin for a few local companies, and got asked a question today that completely stumped me.

You load an Ubuntu pre-release (say, Alpha 1)
and keep it updated all the way through to release date

On the day of official release, is the updated (alpha -> beta -> final) install *guaranteed* to be the same (user config, and system-wide config) as a new install of the final version?

I have a client that develops control software for surveying equipment, and they're looking to target Linux (Ubuntu initially)

They're concerned that if they target Ubuntu, testing on the pre-releases, that they may get differing results when customers load the software on a newly installed final version.

As I said, I just admin their server, so I was a bit stumped by this

Thanks

---

### Post by wayne_cat on 2009-08-14
> **amauk said:**
> Hey ho,

I'm a free-lance sysadmin for a few local companies, and got asked a question today that completely stumped me.

You load an Ubuntu pre-release (say, Alpha 1)
and keep it updated all the way through to release date

On the day of official release, is the updated (alpha -> beta -> final) install *guaranteed* to be the same (user config, and system-wide config) as a new install of the final version?

I have a client that develops control software for surveying equipment, and they're looking to target Linux (Ubuntu initially)

They're concerned that if they target Ubuntu, testing on the pre-releases, that they may get differing results when customers load the software on a newly installed final version.

As I said, I just admin their server, so I was a bit stumped by this

Thanks

Things will change till the final version is available. I started with Alpha 1 and updated
this system ... so it is now an Alpha 4. But I was a little bit surprised when I installed
a fresh Alpha 4 today ... it comes with a new syslog system. My updated Alpha 1 still
uses sysklog but the fresh installed Alpha 4 starts rsyslog. You can not be sure that all
applications in an early Alpha will be available/used in the Final. Maybe your customers
software depends on some other applications (or special versions).

Another problem ... shared libraries ... the Final may/will have new versions ... so 
compatibility may be a problem.

Maybe your customer should talk with Canonical.

---

### Post by psyke83 on 2009-08-15
> **amauk said:**
> On the day of official release, is the updated (alpha -> beta -> final) install *guaranteed* to be the same (user config, and system-wide config) as a new install of the final version?

In theory, yes. In practice, not necessarily.

If you installed from Alpha 1 and continually upgraded, there are several possible issues that may arise, such as the following:

[LIST]
[*]You performed a dist-upgrade which forced an essential or non-essential package to be removed, due to temporary dependency issues (user error, and a surprisingly common occurrence).
[*]Users configurations may not get updated correctly - for example, the configuration of certain GNOME Panel applets may differ when comparing a system upgraded from Alpha 1 vs a fresh installation of Alpha 4. This is because some configuration files are only generated upon the creation of a user account and the first login, and are not always updated when newer versions of the associated software is installed.
[*]During the development process, examplepackage 0.5-0ubuntu1 is released in alpha 1 and causes a problem, and then examplepackage 0.5-0ubuntu2 get uploaded with a fix to the problem. However, package 0.5-0ubuntu3 and onwards no longer contains the fix for the original problematic version (because it was assumed not to be needed anymore). If you try to upgrade from version 0.5-0ubuntu1 to 0.5-0ubuntu3 or later, there will be a problem*.
[*]Considering the ubuntu-desktop metapackage's Recommends/Suggests/Conflicts, different packages may be installed when comparing a fresh install to an upgraded system. If you installed Alpha 1 from scratch, Pidgin gets installed by default. If you install Alpha 4, Empathy gets installed by default instead of Pidgin. If you upgrade from Alpha 1 -> Alpha 4, however, Pidgin will remain installed instead of Empathy (at least I think that's still the case). 
[*]Similar to the point above, Alpha 1 uses GRUB1 as the default bootloader, and in a later alpha it was replaced by GRUB2. You may need to perform manual steps to transition your system from GRUB1 -> GRUB2 (that was true a few weeks ago, I'm not sure if the process is now automatic).
[/LIST]

*This is a silly example, but it's possible that upgrading between development packages may cause unanticipated problems that would never occur when upgrading from a stable release, or performing a fresh install.

To minimize risk when using a system that has been upgraded since an early alpha, make sure:
[LIST]
[*]Only allow packages to be removed (a.k.a a Partial Upgrade) during the development process if you have checked the changelogs for important information in advance, and/or use your common sense.
[*]Upon the final release, wipe your user configuration in-place (use with caution: rm ~/.* -ri), or alternatively, backup your documents and then delete and re-create your user account to ensure that all user configuration and shortcuts are re-created correctly.
[/LIST]

---

### Post by ilna on 2009-08-15
[]("http://ubuntuforums.org/member.php?u=50843")**psyke83**,

You are sharing with us so much valuable information, thanks! Are there some docs "beyond official aptitude guide" (and CLI-oriented rather last one)? I mean some sort of guide(s) of resolving common (and advanced) problems/tasks.

---

### Post by Kobalt on 2009-08-15
You should go trough this : [https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide)
And in the end from a Terminal : ```
man aptitude
```

---

### Post by ilna on 2009-08-15
**Kobalt,**

I'm saying about > docs "**beyond** official aptitude guide" (and CLI-oriented rather last one). I mean some sort of guide(s) of resolving common (and advanced) problems/tasks.As for amptitude, I have a self-printed version of the guide (with zen-related epigraph) ;-)

---

### Post by amauk on 2009-08-15
Thanks for the replies, guys

---

