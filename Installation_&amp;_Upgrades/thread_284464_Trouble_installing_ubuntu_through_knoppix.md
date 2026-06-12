---
title: "Trouble installing ubuntu through knoppix"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by skibler on 2006-10-25
I could not get xubuntu to install on my thinkpad with the alternate install cd, so I am now trying to install it via a knoppix live cd. I am following this guide: [https://help.ubuntu.com/community/Installation/FromKnoppix](https://help.ubuntu.com/community/Installation/FromKnoppix)

Everything has worked up until chrooting. I can chroot in and mount /proc, but the next step fails.
```

Set up base system

Set up the keyboard.

# dpkg-reconfigure console-data

Set up timezones, users, and apt. This is a lengthy process that will try to launch GDM at the end. Of course, GDM can't run because Knoppix already has the screen, but the screen may flash as they fight. 

```
This is what happens:
```
root@Knoppix:/# dpkg-reconfigure console-data
Package `console-data' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: console-data is not installed
root@Knoppix:/#

```

I do not know what this means. Can anyone tell me what is going on here? Thank you.

---

