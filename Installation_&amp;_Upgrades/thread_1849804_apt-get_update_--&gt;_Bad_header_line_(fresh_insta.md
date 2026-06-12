---
title: "apt-get update --&gt; Bad header line (fresh install)"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by Awareness on 2011-09-25
fresh natty install i386 desktop. I get this errors:

```
$ sudo apt-get update
Ign http://extras.ubuntu.com natty InRelease
Ign http://archive.ubuntu.com natty InRelease
Ign http://archive.ubuntu.com natty-updates InRelease
Ign http://archive.ubuntu.com natty-security InRelease
Hit http://extras.ubuntu.com natty Release.gpg
Hit http://extras.ubuntu.com natty Release
Err http://archive.ubuntu.com natty Release.gpg
  Bad header line [IP: 91.189.92.171 80]
Ign http://archive.ubuntu.com natty-updates Release.gpg
Hit http://extras.ubuntu.com natty/main Sources
Err http://archive.ubuntu.com natty-security Release.gpg
  Bad header line [IP: 91.189.92.171 80]
Ign http://archive.ubuntu.com natty Release
Ign http://archive.ubuntu.com natty-updates Release
Hit http://extras.ubuntu.com natty/main i386 Packages
Ign http://extras.ubuntu.com natty/main TranslationIndex
Get:1 http://archive.ubuntu.com natty-security Release [31,4 kB]
Err http://extras.ubuntu.com natty/main Translation-en_US
  Bad header line
Err http://extras.ubuntu.com natty/main Translation-en   
  Bad header line
Get:2 http://archive.ubuntu.com natty-security Release [31,4 kB]                                                                                             
Ign http://archive.ubuntu.com natty/main Sources/DiffIndex
Ign http://archive.ubuntu.com natty/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com natty/universe Sources/DiffIndex
Ign http://archive.ubuntu.com natty/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com natty/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com natty/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com natty/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com natty/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com natty/main TranslationIndex
Ign http://extras.ubuntu.com natty/main Translation-es                                                                                                       
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex                                                                                              
Ign http://archive.ubuntu.com natty/restricted TranslationIndex
Ign http://archive.ubuntu.com natty/universe TranslationIndex
Ign http://archive.ubuntu.com natty-updates/main Sources/DiffIndex
Ign http://archive.ubuntu.com natty-updates/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com natty-updates/universe Sources/DiffIndex
Ign http://archive.ubuntu.com natty-updates/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com natty-updates/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com natty-updates/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com natty-updates/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com natty-updates/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://archive.ubuntu.com natty-security/main Sources/DiffIndex
Ign http://archive.ubuntu.com natty-security/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com natty-security/universe Sources/DiffIndex
Ign http://archive.ubuntu.com natty-security/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com natty-security/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com natty-security/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com natty-security/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com natty-security/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com natty-security/main TranslationIndex
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex
Hit http://archive.ubuntu.com natty/main Sources
Hit http://archive.ubuntu.com natty/restricted Sources
Hit http://archive.ubuntu.com natty/universe Sources
Hit http://archive.ubuntu.com natty/multiverse Sources
Hit http://archive.ubuntu.com natty/main i386 Packages
Hit http://archive.ubuntu.com natty/restricted i386 Packages
Hit http://archive.ubuntu.com natty/universe i386 Packages
Hit http://archive.ubuntu.com natty/multiverse i386 Packages
Hit http://archive.ubuntu.com natty/main Translation-es
Hit http://archive.ubuntu.com natty/multiverse Translation-es
Hit http://archive.ubuntu.com natty/restricted Translation-es
Hit http://archive.ubuntu.com natty/universe Translation-es
Hit http://archive.ubuntu.com natty-updates/main Sources
Hit http://archive.ubuntu.com natty-updates/restricted Sources
Hit http://archive.ubuntu.com natty-updates/universe Sources
Hit http://archive.ubuntu.com natty-updates/multiverse Sources
Hit http://archive.ubuntu.com natty-updates/main i386 Packages
Hit http://archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://archive.ubuntu.com natty-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com natty-security/main Sources
Hit http://archive.ubuntu.com natty-security/restricted Sources
Hit http://archive.ubuntu.com natty-security/universe Sources
Hit http://archive.ubuntu.com natty-security/multiverse Sources
Hit http://archive.ubuntu.com natty-security/main i386 Packages
Hit http://archive.ubuntu.com natty-security/restricted i386 Packages
Hit http://archive.ubuntu.com natty-security/universe i386 Packages
Hit http://archive.ubuntu.com natty-security/multiverse i386 Packages
Ign http://archive.ubuntu.com natty/main Translation-en_US
Ign http://archive.ubuntu.com natty/main Translation-en
Ign http://archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty/multiverse Translation-en
Ign http://archive.ubuntu.com natty/restricted Translation-en_US
Ign http://archive.ubuntu.com natty/restricted Translation-en
Ign http://archive.ubuntu.com natty/universe Translation-en_US
Ign http://archive.ubuntu.com natty/universe Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://archive.ubuntu.com natty-updates/main Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-es
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-es
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://archive.ubuntu.com natty-updates/restricted Translation-es
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com natty-updates/universe Translation-en
Ign http://archive.ubuntu.com natty-updates/universe Translation-es
Ign http://archive.ubuntu.com natty-security/main Translation-en_US
Ign http://archive.ubuntu.com natty-security/main Translation-en
Ign http://archive.ubuntu.com natty-security/main Translation-es
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://archive.ubuntu.com natty-security/multiverse Translation-es
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-security/restricted Translation-en
Ign http://archive.ubuntu.com natty-security/restricted Translation-es
Ign http://archive.ubuntu.com natty-security/universe Translation-en_US
Ign http://archive.ubuntu.com natty-security/universe Translation-en
Ign http://archive.ubuntu.com natty-security/universe Translation-es
Fetched 31,4 kB in 1min 21s (384 B/s)
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg  Bad header line [IP: 91.189.92.171 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg  Bad header line [IP: 91.189.92.171 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_US  Bad header line

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en  Bad header line

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I followed this solution found in google:

```
$ cd /var/lib/apt
$ sudo mv lists lists.old
$ sudo mkdir -p lists/partial
$ sudo apt-get update 
```

but nothing, so i reinsatalled from another iso to see if that was the problem.. its the same. I dont know what to do. :(

I also set default keys with the button found in authentification  in sources dialog... and changed sources from main to my local mirros. Its the same...

i hope the next release is better, because natty has been a huge hindrance from the very beginning :(

any help please? Its frustrating...

---

### Post by Paddy Landau on 2011-09-25
These types of problems usually seem to be transient; that is, there is something wrong with the servers but they are fixed within a few hours.

That, anyway, has been my usual experience.

I'm not sure of the implications of clearing lists the way you did, though. apt-get uses it to clear out obsolete items. It may be an idea to delete your new lists and restore your old one before continuing:
```
$ cd /var/lib/apt
$ sudo rm -R lists
$ sudo mv lists.old lists
```

---

### Post by ajgreeny on 2011-09-25
Use a different server by opening Software-sources and choosing the main server, or your more local one, whichever is not enabled at the moment.  Then try again to update.

---

### Post by Awareness on 2011-09-25
> **Paddy Landau said:**
> These types of problems usually seem to be transient; that is, there is something wrong with the servers but they are fixed within a few hours.

That, anyway, has been my usual experience.

well, if that is so, its been more than 24h since i first got this error, and more people would have complained... so i guess its just me :(

> **Paddy Landau said:**
> 
I'm not sure of the implications of clearing lists the way you did, though. apt-get uses it to clear out obsolete items. It may be an idea to delete your new lists and restore your old one before continuing:
```
$ cd /var/lib/apt
$ sudo rm -R lists
$ sudo mv lists.old lists
```

right now i have a fresh installation...grrr :(

---

### Post by Awareness on 2011-09-25
> **ajgreeny said:**
> Use a different server by opening Software-sources and choosing the main server, or your more local one, whichever is not enabled at the moment.  Then try again to update.

I tried my local server, main server and a server from another country, with the same result :S

---

### Post by Sidewinder1 on 2011-09-25
Awareness, not to hijack your thread but I have been experiencing some "hinky" error messages, related to my 'sources', as well. In my case, it seems to be related to 
[http://www.openprinting.org](http://www.openprinting.org) being unreachable, down, or otherwise useless (with all due respect to the administrators thereof). I wouldn't even mention it but this has been happening for 5 or 6 days, now. That, in conjunction with "kernel.org" experiencing unauthorized access, I'm humbly wondering if there is perhaps a connection. Before you ask, no, I'm not a conspiracy nut. Just a plain old nut; if you don't believe me, just ask my wife.   :D
I'll await your reply, solution, or comments...


Side

---

### Post by Sidewinder1 on 2011-09-25
WOW! I hit 500; guess I'll have to tell her: "Now, ... I'm someone to be reckoned with." ;)

---

