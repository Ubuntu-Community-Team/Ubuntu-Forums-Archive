---
title: "php is no longer run after apt upgrade"
date: 2022-03-12
forum: Installation &amp; Upgrades
---

### Post by rene-veerman-netherlands on 2022-03-12
Hi.

I had PHP on ubuntu 20.04 LTS installed, along with a few other packages like sshd and couchdb, and I was using a custom PPA for PHP.

Along comes apt upgrade, which tells me to run apt autoremove. I see php8 getting removed, and i'm left without any executable php, despite the package 'php' being installed!

What is it with ubuntu getting crippled every 2 years?!

---

### Post by TheFu on 2022-03-13
You'd have to ask the PPA owner.
I haven't seen this, but I'm using the Canonical repos only for my php webapps.

---

### Post by rene-veerman-netherlands on 2022-03-14
Ok, i got it fixed (thanks in part to your help) :)

I simply removed all the PPAs that were serving up "the very latest version" of packages,

then i did (while logged in as root) :
apt remove apache2* php* && apt update && apt install apache2 php php-curl

and this fixed my system :)

---

### Post by TheFu on 2022-03-14
Please help the community by marking this thread as _SOLVED_ - 'thread tools' button near the top of the page.

---

