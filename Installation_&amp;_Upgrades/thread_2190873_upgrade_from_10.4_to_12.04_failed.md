---
title: "upgrade from 10.4 to 12.04 failed"
date: 2013-11-29
forum: Installation &amp; Upgrades
---

### Post by Dan Z on 2013-11-29
Had been running 10.4 and decided to upgrade to 12.04. So initiated via update manager. It ran with lots of apparent problems. 

When it finished, and I rebooted, the GRUB loader still said 10.04, but it started to load 12.04, but it fails rapidly. It starts icecast, it fails, then starts NTP server, fails, then it just stops doing anything.

I can get it to run if I choose 10.4 recover mode, I can log in but nothing further.

So I thought I could use the 12.04 iso and over-write it to fix 12.04, but instead it added a new version of 12.04 on another partition. 

And somehow I ended up with a 3rd copy, on another partition. 

Both of those versions run fine, but the original upgrade does not run, so I am screwed as I can't access my account.

CAn anyone help?

Thanks Dan

---

### Post by mörgæs on 2013-11-29
If you don't have anything of value in the old system:
When installing select 'use entire disk for Ubuntu'. It will erase all the failed installations.

---

