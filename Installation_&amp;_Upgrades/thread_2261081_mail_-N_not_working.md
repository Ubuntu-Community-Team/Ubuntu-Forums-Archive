---
title: "mail -N not working"
date: 2015-01-16
forum: Installation &amp; Upgrades
---

### Post by Tor_Stenvaag on 2015-01-16
I have a server application that uses the command "mail -N". It has been working in Ubuntu server for "I do not know how many years". After an "apt-get dist-upgrade" yesterday this command broke. It now states that an argument is needed. 

$ mail -N
mail: option requires an argument -- 'N'
usage: mail [-dEIinv] [-a header] [-b bcc-addr] [-c cc-addr] [-s subject] to-addr ...
       mail [-dEIiNnv] -f [name]
       mail [-dEIiNnv] [-u user]


When tracking the mail command I end up with 

$ ls -l /usr/bin/bsd-mailx
-rwxr-xr-x 1 root root 97384 Jan  5 18:05 /usr/bin/bsd-mailx

The file is updated 11 days ago.

I am using Ubuntu server 12.04.

Anyone know what might be wrong? I can not find any answer using the man page.

---

### Post by Tor_Stenvaag on 2015-01-16
There is a bug in the latest [COLOR=#000000]bsd-mailx. An option "T" was removed, but the corresponding ":" argument was left in affecting the "N" argument. I have filed a bug.[/COLOR]

---

