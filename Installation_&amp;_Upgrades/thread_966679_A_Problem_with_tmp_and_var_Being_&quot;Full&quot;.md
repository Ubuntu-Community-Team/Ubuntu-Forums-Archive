---
title: "A Problem with /tmp and /var Being &quot;Full&quot;"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by prosario_2000 on 2008-11-01
Recently, I've upgraded from Ubuntu 8.04 to Ubuntu 8.10, and there are some problems with it.  The most serious one that is a bit disruptive has to do with the /tmp file.

For some reason, I'm unable to directly download from websites.  I'm not able to send messages with SwiftDove (a variant of Mozilla-Thunderbird), because it says that the temporary file is full, and similar problems because the /tmp seems to be full.

The funny thing is that even when I clean the /tmp file of most of its content .. it still says is full.  It says that it uses 100% of 1 MB.  The interesting thing is that /tmp is not a separate partition.

Whenever I install something, sometimes I have errors in /var that seem to have the same problem of /var "not having enough space".  For example, this happened when I was installing 3dChess:
> 
(Reading database ... 463126 files and directories currently installed.)
Preparing to replace 3dchess 0.8.1-15 (using .../3dchess_0.8.1-15_amd64.deb) ...
Unpacking replacement 3dchess ...
Processing triggers for man-db ...
/usr/bin/mandb: can't write to /var/cache/man/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/cs/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/de/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/es/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/fi/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/fr.ISO8859-1/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/fr.UTF-8/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/fr/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/gl/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/hu/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/id/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/it.ISO8859-1/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/it.UTF-8/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/it/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/ja/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/ko/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/pa/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/pl.ISO8859-2/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/pl.UTF-8/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/pl/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/pt_BR/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/sr@latin/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/py/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/ru/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/sv/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/tr/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/zh_CN/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/zh_TW/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/de.UTF-8/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/eu/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/sr/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/da/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/lt/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/nl/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/sk/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/vi/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/pt/9041: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/ca_ES@valencia/9041: No space left on device
/usr/bin/mandb: can't create index cache /var/cache/man/oldlocal/9041: No space left on device
/usr/bin/mandb: can't create index cache /var/cache/man/local/9041: No space left on device
Setting up 3dchess (0.8.1-15) ...

I'm using an Intel-64 bit computer. 4 GB RAM, 186.31 GB Hard drive.

/ - 13.97 GB

swap - 3.68 GB

/home - 168.66 GB  (Using 95.32 GB)

I really need this solved quickly.  Any help will be appreciated.

---

### Post by lemming465 on 2008-11-02
Could we get the output of *df -m*

---

