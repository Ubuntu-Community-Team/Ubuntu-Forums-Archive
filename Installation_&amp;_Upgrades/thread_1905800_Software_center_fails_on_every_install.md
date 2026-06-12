---
title: "Software center fails on every install"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by davethewave83 on 2012-01-07
when I try to install a program with the software centre it gets 50% done then fails, sometimes it fails at 80% but it fails every time no matter what I am installing. 

I went to look for the software and it is neither in the software available or software installed location, it went to limbo. 

I figured a purge of the software centre and re-installation of it would fix it, however, when I use Synaptic to purge, it warns me that it is going to remove the "Ubuntu-desktop" which I really don't want to do. 

is there a way to unlink these two things (the ubuntu-desktop and the software centre) or do I need to re-install the entire ubuntu-desktop to repair the problem? 

Thanks :)

---

### Post by mörgæs on 2012-01-08
First you could try to boot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```
Please post the error messages, if any.

---

### Post by davethewave83 on 2012-01-08
> **mörgæs said:**
> First you could try to boot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```
Please post the error messages, if any.

Thanks! Actually I used Synaptic and did a re-install instead of a removal, that fixed it and didn't break gnome-desktop. 

Is there a way to delete my initial post if no one has replied to it?

---

### Post by mörgæs on 2012-01-09
Good, then please mark the thread 'solved'.

In general I would recommend that you forget about Software Centre and use Synaptic. It's fast, have more functionality and it actually works. 

You can edit your posts but not delete them.

---

### Post by davethewave83 on 2012-01-10
> **mörgæs said:**
> Good, then please mark the thread 'solved'.

In general I would recommend that you forget about Software Centre and use Synaptic. It's fast, have more functionality and it actually works. 

You can edit your posts but not delete them.

alright thanks

---

