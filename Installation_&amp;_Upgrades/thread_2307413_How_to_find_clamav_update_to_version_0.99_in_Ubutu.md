---
title: "How to find clamav update to version 0.99 in Ubutu Wiley?"
date: 2015-12-24
forum: Installation &amp; Upgrades
---

### Post by Jay_E on 2015-12-24
Greetings.

i just installed Ubuntu (Mate) 15.10 - Wiley.

I've installed clamav and get the usual line in the log about using an outdated version.
      Thu Dec 24 13:43:45 2015 -> WARNING: Local version: 0.98.7 Recommended version: 0.99

I am now looking for version 0.99.

In the past, I used the backports -- or updates  -- or  a  PPA.

It appears that these are no longer available.

I checked at clamav.net and they offer   the source to go compile.
If I try to compile myself, it is likely that I'll make a mistake somewhere (after spending hours..)

Is there a pre-compiled '.deb' file somewhere that I can install?

I checked the Ubuntu Package search...
 0.98.7+dfsg-0ubuntu4: amd64 i386    exists in Wiley
  No clamav in Wiley-backports   or Wiley-Updates (on 24 Dec 2015).

Thanks in advance!!

Jay ):P


ps I tried an update but it is still 0.98
as:
Package clamav:                        
[FONT=courier new]p   0.98.7+dfsg-0ubuntu4     wily            500 
i   0.98.7+dfsg-0ubuntu5                     100 

[/FONT]The .deb was from [https://launchpad.net/ubuntu/xenial/i386/clamav/0.98.7+dfsg-0ubuntu5](https://launchpad.net/ubuntu/xenial/i386/clamav/0.98.7+dfsg-0ubuntu5)

Thanks again!!

---

### Post by ian-weisser on 2015-12-24
Version number confusion.
Debian and Ubuntu ensure that ClamAV, regardless of the version number, has the latest data.

The version number is different because upgrading ClamAV natively is *different* from upgrading through Debian/Ubuntu.
Version numbers have a meaning that is different to the package manager than to you.
So the version numbers often don't match...but ClamAV is still up to date.

---

### Post by Bucky Ball on 2015-12-25
You only need to update the definitions. That is the important bit. The version is, in some ways, a bit irrelevant. As long as you have the latest virus definitions, you're good to go.

```
sudo freshclam
```

---

