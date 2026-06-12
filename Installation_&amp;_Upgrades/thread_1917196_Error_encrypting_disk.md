---
title: "Error encrypting disk"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by diebodie on 2012-01-29
Whilst I was installing my system, I neglected to encrypt the disk, an error I'm starting to regret. I'm folowing this guide to no avail. [http://www.makeuseof.com/tag/encrypt-home-folder-ubuntu-installation-linux/](http://www.makeuseof.com/tag/encrypt-home-folder-ubuntu-installation-linux/)

> [QUOTE]cam@jewbear-desktop ~ $ sudo su
[sudo] password for cam: 
jewbear-desktop cam # ecryptfs-migrate-home –u jewbear

Usage:

/usr/bin/ecryptfs-migrate-home -u USER

 -u,--user       Migrate USER's home directory to an encrypted home directory

WARNING: Make a complete backup copy of the non-encrypted data to
another system or external media. This script is dangerous and, in
case of an error, could result in data lost, or lock you out of your
system!

This program must be executed by root.


jewbear-desktop cam # /usr/bin/encryptfs-migrate-home -u jewbear
bash: /usr/bin/encryptfs-migrate-home: No such file or directory


[/QUOTE]

jewbear-desktop cam # wtf???!! I am root.. folowing instructions are moot. -_- 

I looked in /usr/bin and there is indeed a encryptfs-migrate-home file.. Tried running it in terminal to no avail..

---

