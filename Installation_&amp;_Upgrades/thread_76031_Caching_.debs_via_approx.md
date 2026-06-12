---
title: "Caching .debs via approx"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by sjoh_64 on 2005-10-14
Hi all,

my first post to this forum, my first day using ubuntu!

I have the following problem: To save bandwith and avoid redownloading software on both my computers, I have setup one to be an apt-proxy via appox. Approx was configured to use [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) and [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) as backends and at first seemed to work fine.

But now I get the following errors upon apt-get update:

Get:1 [http://localhost](http://localhost) breezy Release.gpg [189B]
Get:2 [http://localhost](http://localhost) breezy-updates Release.gpg [189B]
Get:3 [http://localhost](http://localhost) breezy-security Release.gpg [189B]
Hit [http://localhost](http://localhost) breezy Release
Ign [http://localhost](http://localhost) breezy Release
Hit [http://localhost](http://localhost) breezy-updates Release
Hit [http://localhost](http://localhost) breezy-security Release
Ign [http://localhost](http://localhost) breezy-updates Release
Hit [http://localhost](http://localhost) breezy/main Packages
Hit [http://localhost](http://localhost) breezy/restricted Packages
Hit [http://localhost](http://localhost) breezy/universe Packages
Hit [http://localhost](http://localhost) breezy-updates/main Packages
Hit [http://localhost](http://localhost) breezy-updates/restricted Packages
Hit [http://localhost](http://localhost) breezy-security/main Packages
Hit [http://localhost](http://localhost) breezy-security/restricted Packages
Hit [http://localhost](http://localhost) breezy-security/universe Packages
Fetched 567B in 2s (264B/s)
Reading package lists... Done
W: GPG error: [http://localhost](http://localhost) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://localhost](http://localhost) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

Running apt-get update again does not help. If I revert my sources.list back to the original one, bypassing the proxy, no errors are displayed.

How can I configure apt-get to correctly gpg-verify packages received through my local apt-proxy?

Thanks for your help!

---

### Post by krappy on 2005-10-18
I have the same problem, and from the apt-proxy mailling list archive, it seems that currently apt-proxy2 can not handle the gpg signed packages properly.
Here is the link if you are interested

[http://sourceforge.net/mailarchive/forum.php?thread_id=7967488&forum_id=7622](http://sourceforge.net/mailarchive/forum.php?thread_id=7967488&forum_id=7622)

---

