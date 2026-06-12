---
title: "error updating some 8.04 servers"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by ezacon on 2008-10-14
I have 2 sites with an ubuntu 8.04 as gateways in each site.
In one site, i can update server, but in the second site with the same sources.list and apt.conf y get this error:

Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/restricted Translation-es
Obj [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-backports/main Translation-es
99% [1 Translation-es bzip2 0] [Esperando las cabeceras]
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main Translation-es
67% [2 Translation-es bzip2 0] [Esperando las cabeceras]


This error is fron an apt-get update command.
It is not related to sources.list, because i use the exact same file in both servers. I have already tryed with different county proxies in sources.list with same result.

Some times, after one of these error during apt-get update, the server hangs for a couple a minutes and continues with update but with more errors.
It is not a network issue, because i have downloaded realy large files (>400Mb) with wget without problem.

I am realy lost with this one.
Any idea?

Thanks

---

### Post by ezacon on 2008-10-14
according to some posts i have tried this:

unset LANG
apt-get update

Now i can complete the command and the system does not hang, bun pauses for several minutes before completing.
I can update the system, but with lots of pauses in the downloading (no percent progress).

It has to do with apt proxy and locales, but i use direct mirrors without proxies... ?

---

