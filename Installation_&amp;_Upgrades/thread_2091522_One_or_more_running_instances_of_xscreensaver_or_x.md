---
title: "One or more running instances of xscreensaver or xlockmore have been detected on this"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by skyemoor on 2012-12-05
Dell Latitude 630

Upgrading from Ubuntu 11.10 Oneiric Ocelet to 12.04

Received this warning during install;

"One or more running instances of xscreensaver or xlockmore have been detected on this system. Because of incompatible library changes, the upgrade of the GNU libc library will leave you unable to authenticate to these programs. You should arrange for these programs to be restarted or stopped before continuing this upgrade, to avoid locking your users out of their current sessions. "

I opened task manager, found one instance of xscreensaver, killed it, found none of xlockmore, and proceeded with the install.

It then gave me what seemed to be a follow-up script to clean up after the install;

"rsync cups cron atd apache2"

However, it will not run in terminal mode.

What should I do?

---

