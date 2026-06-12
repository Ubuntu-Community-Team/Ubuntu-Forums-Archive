---
title: "I'm not supposed to use root, but..."
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by mikeymikec on 2006-06-08
I couldn't find anything about how to get admin-privs-required tasks done, for example I wanted to change where an NTFS partition is mounted, but I kept getting 'permission denied' for viewing, for example, the folder contents of /mnt.

I did a bit of googling and found how to get into the root account on a new ubuntu installation.  Then I read a bit about "you shouldn't use root at all"... if the user I created during installation is an admin-capable user, then why can't it do basic things (like modifying permissions on say /mnt so that users like myself can read the directory)?

I'm a Linux newbie (despite trying quite a few distros in the past and never settling with any for long, I'm quite impressed with Ubuntu though!).  I'd say I've been promoted from 'FreeBSD newbie' status to 'FreeBSD novice', but the majority of my experience is with Windows.

I'll have a whole bunch of other questions, like what the best way of changing the screen resolution to an option that isn't listed in the 'screen resolution' program... it only lists 1024x768 or less, and only 60Hz, which will give me eye cancer if I look at it for much longer.  1280x1024x85Hz please!

---

### Post by 23meg on 2006-06-08
Meet sudo.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

For screen resolution, see [this thread]("http://ubuntuforums.org/showthread.php?t=83973").

---

### Post by nanotube on 2006-06-08
[QUOTE=23meg]Meet sudo.
[/QUOTE]
hehe, nice way of putting it. ;)

---

### Post by aysiu on 2006-06-08
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) might also help.

---

