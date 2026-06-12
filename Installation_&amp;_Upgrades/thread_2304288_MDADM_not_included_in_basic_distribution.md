---
title: "MDADM not included in basic distribution?"
date: 2015-11-25
forum: Installation &amp; Upgrades
---

### Post by ejoftheweb on 2015-11-25
I don't know exactly when, but at some time mdadm seems to have been removed from the basic distro. Or something. In any case, the problem is that following an upgrade I have to rebuild my RAID array, which is annoying. I'm sure I didn't have to do this in the past - but having just upgraded from 14.04 to 15.04 there is no sign of /dev/md0, and I need to reinstall mdadm and rebuild the array. 

I recognise that as the distribution grows, the complexity of maintaining a smooth upgrade path for all the possible variations grows exponentially. But utilities like mdadm ought, in my opinion, to be at the heart of the distribution. It's not as if it's particularly big - it's 1.5M including postfix, which isn't really a dependency but comes from an assumption that RAID is only used on big servers.  Now that the CD-ROM 650M  size limit is well and truly busted, the size of the distro ISO isn't that critical, and in any case we could surely dump loads of other bloaty stuff like Thunderbird.

---

### Post by Bashing-om on 2015-11-25
ejoftheweb; Hello;

Mind you there is a bunch I do not know and even more I take for granted .
I see it as raid is a server function, and having it on a desktop install for a novice user will but confuse the issue of installation.
The tool is easily installed for the desktop:
```

sudo apt-get install dmraid

```
on a fully updated system.

See the documentation ' /usr/share/doc/dmraid ' .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

