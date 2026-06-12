---
title: "Stuck in command line after upgrading to 16.04"
date: 2016-08-30
forum: Installation &amp; Upgrades
---

### Post by zeroexcelcior on 2016-08-30
I was running Ubuntu 14.04 gnome flashback (metacity) before letting the update manager upgrade to 16.04. Ubuntu now only boots to command line. After logging in, the following error appears:

-bash: cannot create temp file for here-document: Read-only file system

It looks like the operating system partition got switched to read only at some point but I don't know what to do to fix that or if it's even related. I can live boot from a flashdrive without issue. I would prefer to not have to perform a clean install to fix.
Thank you all in advance.

---

### Post by reese1379 on 2016-09-01
Boot from the flashdrive and then type [COLOR=#111111][FONT=Consolas]sudo fsck -Af -M at the BASH prompt[/FONT][/COLOR]

---

### Post by zeroexcelcior on 2016-09-01
Thanks for the reply, reese. However after 24 hours without a response I successfully attempted to recover the files I wanted from the affected partition and tried a clean install of 16.04. After some troubleshooting I found that the hard drive I had been using was on its way out and I suspect that is why Ubuntu was unable to properly do what it needed to do.

---

