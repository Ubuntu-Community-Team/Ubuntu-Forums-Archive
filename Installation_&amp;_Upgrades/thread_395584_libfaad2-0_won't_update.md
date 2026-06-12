---
title: "libfaad2-0 won't update"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by mtrim on 2007-03-28
This problem isn't really serious, it's just annoying. A couple days after upgrading to feisty, libfaad2-0 appeared in the list of upgradeable packages in adept. The problem is when I actually do the upgrade libfaad2-0 doesn't get installed or something. Therefor, adept is now permanently notifying me that there are new updates to install. So now I don't know if there actually are new upgrade or if its just that one stupid package! Anyone have any ideas?

Oh in case this is helpful, which is probably isn't... here is the output that apt-get gives:

```

The following packages have been kept back:
  libfaad2-0
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

---

### Post by RagingOcelot on 2007-06-27
I've been having this same problem for the past couple of days.  It sure is annoying to permanently see the Adept icon in my tray.  I believe libfaad0 and libfaad2-0 aren't getting along.  Fact, I think it's one and the same package. 

When I tried to install the Debian package libfaad0_2.5-4_i386.deb, I get:

```
dpkg: considering removing libfaad2-0 in favour of libfaad0 ...
dpkg: no, cannot proceed with removal of libfaad2-0 (--auto-deconfigure will help):
 faad depends on libfaad2-0 (>= 2.0.0+cvs20060416)
  libfaad2-0 is to be removed.
dpkg: regarding libfaad0_2.5-4_i386.deb containing libfaad0:
 libfaad0 conflicts with libfaad2-0 (<< 2.5-4)
  libfaad2-0 (version 2.0.0+cvs20060416-0.3v1ubuntu0) is installed.
dpkg: error processing libfaad0_2.5-4_i386.deb (--install):
 conflicting packages - not installing libfaad0
Errors were encountered while processing:
 libfaad0_2.5-4_i386.deb
```

The first line makes me think this problem will be resolved eventually.

---

