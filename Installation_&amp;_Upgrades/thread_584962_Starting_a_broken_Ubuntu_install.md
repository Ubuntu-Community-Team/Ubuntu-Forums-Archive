---
title: "Starting a broken Ubuntu install"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by johantmn on 2007-10-21
Hi, I'm a ubuntu novice who has gotten himself into some start-up trouble. I'm running Ubuntu on my old laptop ( GRUB dual-boot with Xp as secondary OS) and the CD-rom drive doesn't work anymore.
 My problem is that the other night as I was upgrading  Ubuntu to 7.10 the laptop ran out out power and turned off while installing. Now Ubuntu isn't starting properly anymore, my username and password is accepted but it all ends i a light blue screen where I can't do anything.
I guess that, since I can still log in Ubuntu is stille there somewhere but I just don't know how to get in, and since my cd-rom drive doesn't work I can't just reinstall it.

Hope there is some help outthere.

Johantmn

---

### Post by Dr. Nick on 2007-10-21
have you tried selecting recovery mode from grub? If you can get in to the command line run

sudo apt-get dist-upgrade

That will restart the upgrade, it may tell you a error and the solution to fix it

---

