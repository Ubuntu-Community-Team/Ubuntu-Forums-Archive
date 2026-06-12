---
title: "Auto security updates"
date: 2016-11-27
forum: Installation &amp; Upgrades
---

### Post by johnmne on 2016-11-27
1. How do I configure the frequency of auto security updates?

I know it's related to the package "unattended-upgrades".
But the file "/etc/apt/apt.conf.d/50unattended-upgrades" is full with comments (lines starting with "//").

2. How do I make sure that automatic updates do occur?
The file "/var/log/apt/history.log" shows that "/usr/bin/unattended-upgrade" works every 2-3 days which seems like a lot.
By reading the "Software Updater" app I see that there are security updates available which weren't installed.

In _Software & Updates_, under the _Updates_ tab:
The field "When there are security updates: " is set to the value "Download and install automatically".
Also all checkboxes at the top (below "Install updates from: ") are checked (with a V ).

Ubuntu 16.04.

---

### Post by ian-weisser on 2016-11-27
apt has background jobs that run daily whether you like it or not - they are triggered by a daily cron job.
For security updates, this is generally considered a good idea.
To have one background job (like unattended-upgrade) run less frequently, you must change a setting hidden deep within /usr/lib/apt/apt.systemd.daily. I have not tried it, and am unsure if that setting even works anymore.

1) /etc/apt/apt.conf.d/50unattended-upgrades tells apt which repositories to use. It doesn't handle frequency.
The xenial-security repository should not be commented. If it is, uncomment it.

2) Couple answers to your question.

```

// Timestamp file - see if unattended-upgrade is working at all.

$ ls -l **/var/lib/apt/periodic**
total 0
-rw-r--r-- 1 root root 0 Nov 22 19:47 autoclean-stamp
-rw-r--r-- 1 root root 0 Nov 27 08:08 download-upgradeable-stamp
-rw-r--r-- 1 root root 0 Nov 27 08:08 **unattended-upgrades-stamp**
-rw-r--r-- 1 root root 0 Nov 27 08:08 update-stamp
-rw-r--r-- 1 root root 0 Nov 27 08:08 update-success-stamp
-rw-r--r-- 1 root root 0 Nov 27 08:08 upgrade-stamp



// Logfile - see what unattended-upgrade is doing, and look for errors.

$ tail **/var/log/unattended-upgrades/unattended-upgrades.log**
2016-11-26 07:23:41,616 INFO Initial blacklisted packages: 
2016-11-26 07:23:41,617 INFO Initial whitelisted packages: 
2016-11-26 07:23:41,617 INFO Starting unattended upgrades script
2016-11-26 07:23:41,617 INFO Allowed origins are: ['o=Ubuntu,a=yakkety-security']
2016-11-26 07:23:46,094 INFO No packages found that can be upgraded unattended and no pending auto-removals
2016-11-27 08:08:23,346 INFO Initial blacklisted packages: 
2016-11-27 08:08:23,364 INFO Initial whitelisted packages: 
2016-11-27 08:08:23,364 INFO Starting unattended upgrades script
2016-11-27 08:08:23,364 INFO Allowed origins are: ['o=Ubuntu,a=yakkety-security']
2016-11-27 08:08:26,638 INFO No packages found that can be upgraded unattended and no pending auto-removals



// unattended-upgrade runs at a random time each day.
// If your system is suspended or off, the job will run a few minutes after resume. Some people mistake this for "the job didn't run at all one day"

$ systemctl list-timers apt-daily.timer

**NEXT**                         LEFT     **LAST **                        PASSED       UNIT            ACTIVATES
**Mon 2016-11-28 05:13:31 CST**  17h left **Sun 2016-11-27 08:07:50 CST**  3h 10min ago apt-daily.timer apt-daily.service

1 timers listed.
Pass --all to see loaded but inactive timers, too.

```

Note that many available upgrades are NOT security upgrades. They are not in the -security repo, and won't be picked up by unattended-upgrade (unless you change the settings). When you see upgrades that are not automatically installed, check the repo they are coming from, too.

---

### Post by johnmne on 2016-11-28
1) The xenial-security repo isn't commented:
From "/etc/apt/sources.list":
```
deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

```

Thank you for the elaborate response!
Ubuntu is quite confusing, there are many methods to treat the same thing..

---

### Post by Dennis N on 2016-11-28
The suggestion was to check **/etc/apt/apt.conf.d/50unattended-upgrades** (that's not the file used in your display)
You did say that the file 50unattended-upgrades was "full of comments", so be sure to check it.
It should start like this in the default installation:
```
dmn@Sydney:/etc/apt/apt.conf.d$ cat 50unattended-upgrades 
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"${distro_id}:${distro_codename}";
	"${distro_id}:${distro_codename}-security";
//	"${distro_id}:${distro_codename}-updates";
//	"${distro_id}:${distro_codename}-proposed";
//	"${distro_id}:${distro_codename}-backports";
};

```
the // are used for the "comment" lines here.

---

