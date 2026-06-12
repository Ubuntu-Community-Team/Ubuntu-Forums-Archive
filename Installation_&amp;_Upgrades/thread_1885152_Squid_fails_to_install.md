---
title: "Squid fails to install"
date: 2011-11-22
forum: Installation &amp; Upgrades
---

### Post by Van Staay on 2011-11-22
Hi everyone,

I installed Ubuntu Server 8.10 on a VMware.
I configured 2 NIC's and they can ping with the internet.
When i wanted to install SQUID, i hit a brickwall.. even after looking on the web for answers..

1) Sudo apt-get update
I get a connection with [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com), but after some time, it seems that there is a disconnection (failed to fetch).  Very similar as this post : [http://ubuntuforums.org/showthread.php?t=1315142](http://ubuntuforums.org/showthread.php?t=1315142)
2) apt-get update -o Acquire::http::No-Cache=True
This also fails.  I can ping "us.archive.ubuntu.com".

3) sudo aptitude update gives also an error.
4) sudo apt-get install squid.  The error is "E: couldn't find package squid.

5) I change/edit the "http's to ftp's in /etc/apt/source.list and try again " apt-get install update", or apt-get update or apt-get install squid...
Nothing works.


Any idea what can cause this issue ?
Greetings,
Carl

---

### Post by dniMretsaM on 2011-11-22
8.10 is no longer supported and it's repositories have been disabled. You'll need to install a new version. 10.04 is the current LTS, 11.10 is the latest.

---

### Post by gmargo on 2011-11-22
8.10 Intrepid is no longer supported or updated.

However, you can still install everything from that release. The repositories were only moved, not removed.

You will have to manually edit your **/etc/apt/sources.list** file.

Change all instances of:
"http://us.archive.ubuntu.com/ubuntu/ intrepid"
to
"http://old-releases.ubuntu.com/ubuntu/ intrepid".

Modify similarly for "intrepid-updates" or "intrepid-backports" entries.

The security entries are slightly different:
Change all instances of:
"http://security.ubuntu.com/ubuntu intrepid-security"
to
"http://old-releases.ubuntu.com/ubuntu/ intrepid-security".

Now a normal "apt-get update" etc should work.

---

