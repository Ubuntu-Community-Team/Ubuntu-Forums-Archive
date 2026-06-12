---
title: "apt-get ... where did my files go?"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by qcarver on 2008-06-17
Aloha,

I'm using Ubuntu 8.04 and I've got some confusion about apt-get.

if I:
apt-get install libopenal-dev

and then:
apt-file list libopenal-dev

I see that I got:
...blah blah blah....
libopenal-dev: /usr/lib/libopenal.a
libopenal-dev: /usr/lib/libopenal.la
libopenal-dev: /usr/lib/libopenal.so
..blah blah blah...

however, if I list my /usr/lib (and /usr/local/lib) I do not see the files there.

Isn't the point of apt-get to put the files in the directories? Or am is this a personal understanding issue?

btw: I tied some other stuff, like removing and reinstalling, installing the package name followed by + and -. Removing the package with --purge, and then reinstalling.

Mahalo Nui Loa,
Quinn

---

