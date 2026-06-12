---
title: "Server upgrade weirdness"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Trunkles on 2011-04-29
So, I tried a do-release upgrade again and got this...

Get:1 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) natty/universe libnspr4-0d i386 4.8.7-0ubuntu1 [13.8kB]
Fetched 13.8kB in 0s (0B/s)

Upgrading
Fetched 0B in 0s (0B/s)
Reading changelogs... Done
  The postinst-script has been updated to set stricter permissions on some
  directories (/var/lib/amavis and subdirs) as suggested by the upstream
  maintainer. This may lead to errors when running certain virus scanners or
  webfrontends for quarantine management. If you run into problems after
  upgrading please look into README.Debian for hints how to solve them.

 -- Harald Jenny <harald@a-little-linux-box.at>  Tue, 24 Nov 2009 17:05:06 +0100

apt (0.8.11) unstable; urgency=low

  * apt-get install pkg/experimental will now not only switch the
    candidate of package pkg to the version from the release experimental
    but also of all dependencies of pkg if the current candidate can't
    satisfy a versioned dependency.

 -- David Kalnischkies <kalnischkies@gmail.com>  Fri, 03 Dec 2010 14:09:12 +0100

fail2ban (0.8.4-3) unstable; urgency=low

  * Jail named-refused-udp is unsafe and opens possibility for easy DoS,
    thus discouraged to be used, and commented out (see #583364 for more
    information).

 -- Yaroslav Halchenko <debian@onerussian.com>  Mon, 28 Jun 2010 22:12:22 -0400

pam (1.1.2-1) unstable; urgency=low

  * Name of option for minimum Unix password length has changed

:

The : at the end is a prompt of some sort.

I'm seriously puzzled folks! What the hell do I do now!

I'd change to the main server rather than the local NZ one, but I have no idea what to put in sources.list.

And the do-release-upgrade killed the cursor in PuTTY.

HELP! :D 
Simon.

---

