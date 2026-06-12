---
title: "Problem upgrading Edgy to Feisty"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by Tom9999 on 2007-08-09
I am trying to upgrade Edgy to Feisty using the update manager however in the initial stages I get the message 

"Failed to fetch ttp://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)"

Can anyone explain this to me?

---

### Post by Kralizec on 2007-08-09
Something like this happened to a lot of people if I'm not mistaken...I think a solution that most people found was to go into their /etc/apt/sources.list and modify all URLs to be ftp instead of http; for example:

```

deb **http**://archive.ubuntu.com/ubuntu/ feisty main restricted

```
would become
```

deb **ftp**://archive.ubuntu.com/ubuntu feisty main restricted

```
and so on for all of the sources. 

I had a lot of problems like the one you described but as I was trying to upgrade on a school computer that I wouldn't even have later, I just decided to download the Feisty live cd and install from there, but I heard changing from http to ftp worked for a lot of people.

---

