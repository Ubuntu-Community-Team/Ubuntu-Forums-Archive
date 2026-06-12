---
title: "Update Error"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by leonardose on 2012-06-08
Friends I'm having problems when I type: apt-get update.
 Being that I'm just having terminal access and so I am trying to update the apt and then find the package VNC.
 I'm using:
 Natty'12 .04 '

 [I][B]Error:
[/B][/I]```
root@localhost:# apt-get update
Ign http://ports.ubuntu.com natty InRelease        
Ign http://ports.ubuntu.com natty-security InRelease
Hit http://ports.ubuntu.com natty Release.gpg
Hit http://ports.ubuntu.com natty-security Release.gpg
Hit http://ports.ubuntu.com natty Release
Hit http://ports.ubuntu.com natty-security Release
Hit http://ports.ubuntu.com natty/main Sources  
Hit http://ports.ubuntu.com natty-security/main Sources
W: Failed to fetch  http://ports.ubuntu.com/ubuntu-ports/dists/natty/Release  Unable to find  expected entry 'non-free/source/Sources' in Release file (Wrong  sources.list entry or malformed file)

W: Failed to fetch  http://ports.ubuntu.com/ubuntu-ports/dists/natty-security/Release   Unable to find expected entry 'non-free/source/Sources' in Release file  (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```I think it's something to sources.list, has researched on various topics not solve.

***Sources.list:***
```
deb http://ports.ubuntu.com/ubuntu-ports natty main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports natty main non-free
deb http://ports.ubuntu.com/ubuntu-ports natty-security main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports natty-security main non-free

```wanted some help on how to solve,
 thank you.

---

### Post by Old_Grey_Wolf on 2012-06-09
Comment out (#) these two lines in the sources.list. There is no non-free in those repositories. I also doubt you need the source code either.

```
deb-src http://ports.ubuntu.com/ubuntu-ports natty main non-free
deb-src http://ports.ubuntu.com/ubuntu-ports natty-security main non-free
```

---

