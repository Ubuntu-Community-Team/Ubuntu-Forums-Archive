---
title: "Problem with APT-GET"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by Kims0r on 2012-11-14
Hi folks,

since today I have a problem with apt-get on my Ubuntu-Linux Server which runs VMWare Server with two VMs:

lsb_release -a:
Distributor ID: Ubuntu
Description:    Ubuntu 9.10
Release:        9.10
Codename:       karmic

uname -a:
Linux tick 2.6.31-17-server #54-Ubuntu SMP Thu Dec 10 18:06:56 UTC 2009 x86_64 GNU/Linux

When I tried to install a few things like "sudo apt-get install gnome-system-tools" I got a lot of 404s for I would say everything he tried to get, also a "sudo apt-get update" just spitted out 404s.

Internet connection of course is fully fuctioning and fast (100MBit/s) I'm connected over SSH cmd line.

All I found in forums over the afternoon did not fit to my problem. Is it so easy that I should know?
What Infos do you need to help me? I have to update & install! :)

Thanks in advance,

Kim

---

### Post by SlugSlug on 2012-11-14
9.10 is end of life

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You'd need to upgrade your distro - best picking an LTS version

---

### Post by QIII on 2012-11-14
+1 to SlugSlug.  The 404s mean that the repos have been moved and archived because that version is no longer supported.

You *can actually* find the older repos for older releases, but there is great danger in using such an old version.

If you absolutely must use 9.10, let us know and we will help you find the old repos and install what you want.  That is, after all, what you asked for help with.

But I really want to recommend strongly against that.

---

