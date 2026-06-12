---
title: "upgrade from dapper to hardy  failing (dmsetup would break udev)"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by wazzup on 2008-07-15
When upgrading from dapper to hardy I get the following error:


dpkg: regarding .../dmsetup_2%3a1.02.20-2ubuntu2_i386.deb containing dmsetup:
 dmsetup breaks udev (<< 113-0ubuntu1)
  udev (version 079-0ubuntu35) is present and installed.
dpkg: error processing /var/cache/apt/archives/dmsetup_2%3a1.02.20-2ubuntu2_i386.deb (--unpack):
 installing dmsetup would break udev, and
 deconfiguration is not permitted (--auto-deconfigure might help)
(Reading database ... 61952 files and directories currently installed.)

....

Errors were encountered while processing:
 /var/cache/apt/archives/dmsetup_2%3a1.02.20-2ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

the only reference I found is alas in Japanese:

[http://vori-misc.blogspot.com/2008/07/ubuntu-dapper-hardy.html](http://vori-misc.blogspot.com/2008/07/ubuntu-dapper-hardy.html)

I believe they are suggesting to remove udev, but who knows what's hidden in the kanji, katakana and hiragana.

---

### Post by wazzup on 2008-07-15
update:

ok, so I removed udev

# aptitude remove udev

after which a whole lot of things happened. Eventually I got a working system with apparently only lvm2 withheld. When I went into aptitude though I saw another 14 broken packages. With a lot of work I resolved all these problems and finally lvm2 was finally fixed.

I then removed some old stuff with orphaner (deborphan, wonderful tool) and did a reboot.

I got a whole lot of

    device-mapper: table: 245:1: linear: dm-linear: device lookup failed

which were resolved by removing evms as per [http://ubuntuforums.org/showthread.php?t=587450](http://ubuntuforums.org/showthread.php?t=587450)

this still left me with a broken exim and apache, and a whole lot of packages that needed to be installed.


Anyways, problem is gone, but it is apparent that upgrading from one LTS to the next is not that easy as I thought it would be.

This was all on a clean test-server, so I won't try this on my production servers anytime soon.

---

### Post by michaelcoburn on 2008-08-04
confirm first that your system doesn't require device-mapper via the mount command, and look for any /dev/dm- entries.  if none, then you should be safe to:

apt-get remove dmsetup

Then you should be able to re-run apt-get dist-upgrade and it should go flawlessly.

This procedure worked for me from 6.06 -> 8.04.

Edit: you _probably_ shouldn't be removing udev, lots of stuff depend on it.  better to remove dmsetup.

---

### Post by donco on 2009-10-30
> **michaelcoburn said:**
> confirm first that your system doesn't require device-mapper via the mount command, and look for any /dev/dm- entries.  if none, then you should be safe to:

apt-get remove dmsetup

Then you should be able to re-run apt-get dist-upgrade and it should go flawlessly.

This procedure worked for me from 6.06 -> 8.04.

Edit: you _probably_ shouldn't be removing udev, lots of stuff depend on it.  better to remove dmsetup.

NOTE:  lvm2 also requires dmsetup

I had to dpkg -r dmsetup and lvm2 as well as a few other packages before I got going again.

Very, very frightening given that LVM is *in use*, but so far so good (just have to install them again on the tail end, I hope).

This is a server which provides rudimentary services (no X et al).  Seeing this mess, I wouldn't even consider doing an "upgrade" on my desktop.  It'll be far easier to simply do a fresh install (what would likely end up happening anyway).

That's all for now.  I'll edit with any updates as they occur (at work watching this unfold on my headless server at home).

Regards,
-the donco

---

### Post by donco on 2009-10-30
Almost forgot to [re]install lvm2 at the end -- I shudder to think of the nightmare that would have started.

While I was at it, I checked and didn't find any other lvm packages (like a newer lvm3).

Worked like a champ.  Noted that /proc/mdstat shows the "dm-" names rather than physical hd's (hda, hdb, ..., hdg, hdh), but everything works fine at present.

Regards,
-the donco

---

