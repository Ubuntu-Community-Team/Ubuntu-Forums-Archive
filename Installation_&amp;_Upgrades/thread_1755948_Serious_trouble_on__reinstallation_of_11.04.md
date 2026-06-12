---
title: "Serious trouble on  reinstallation of 11.04"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2011-05-11
I had installed 11.04 and whilst it was working I had trouble with a usb stick drive. I could not copy to it or easily delete files. I thought my system was corrupted. 

I decided I had better do a reinstall. On starting normally it did not load. Loading via safe mode the result appears awful. What should I do.

> Modprobe:FATAL: could not load /lib/modules/2.6.38-9 generic-pae/modules.dep: no such file or directory.

Mount: unknown filesystem type 'reiserfs'

Mountall: mount /media/g [860] terminated with status 32

filesystem could not be mounted /media/g

INIT: unreadahead-other main process (886) terminated status 4

My home directory is on a separate partition.

Is it possible to get my original installed programs using the live cd, using dpkg --get-selections > installed-software


I am guessing I will have to do a clean install. But before that what should I do?

---

### Post by Robbyx on 2011-05-11
I can see what part of the problem is:

Modprobe:FATAL: could not load /lib/modules/2.6.38-9 generic-pae/modules.dep: no such file or directory.

Whats in there is 2.6.38-8

I will try downloading unbuntu again and hopefully it is the latest version.

---

