---
title: "Can't install and CAN'T remove anything, same error (buntu 14.10)"
date: 2014-12-23
forum: Installation &amp; Upgrades
---

### Post by virakocha on 2014-12-23
Can't install and CAN'T remove anything, same error (buntu 14.10). When I used ' sudo apt-get install -f ', this came :  

```
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 80 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up icedtea-netx:amd64 (1.5.1-1ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: error: alternative path /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/javaws doesn't exist
dpkg: error processing package icedtea-netx:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 icedtea-netx:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


This part is same for every install. 

```
Errors were encountered while processing:
 icedtea-netx:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2014-12-23
virakocha; Hi ! Welcome to the forum.



Not really sure, yet, what should be done here.
see:
```

apt-cache show icedtea-netx

```
I think the place to start at is to try and remove the utility:
```

sudo apt-get purge icedtea-netx

```

Maybe we need then to update java; per the advisory:
> 
Depends: openjdk-7-jre | openjdk-6-jre (>= 6b23~pre10~), icedtea-netx-common (>= 1.5-1ubuntu1)


What is installed ? :
```

dpkg -l openjdk-7-jre 
dpkg -l openjdk-6-jre

```

see iffen we can finger this
[INDENT][INDENT][INDENT]sloppyation out
[/INDENT][/INDENT][/INDENT]

---

### Post by schragge on 2014-12-23
Also, have a look at [thread=2257828]this thread[/thread]. Seems like the same problem to me.

---

### Post by virakocha on 2014-12-23
> **Bashing-om said:**
> virakocha; Hi ! Welcome to the forum.



Not really sure, yet, what should be done here.
see:
```

apt-cache show icedtea-netx

```
I think the place to start at is to try and remove the utility:
```

sudo apt-get purge icedtea-netx

```

Maybe we need then to update java; per the advisory:


What is installed ? :
```

dpkg -l openjdk-7-jre 
dpkg -l openjdk-6-jre

```

see iffen we can finger this[INDENT][INDENT][INDENT]sloppyation out
[/INDENT]
[/INDENT]
[/INDENT]




Worked. Fabulous. Thank you. I'm new to Ubuntu, installed it yesterday and it is great

---

### Post by Bashing-om on 2014-12-23
virakocha; Great !

Pleased for the nuance all is good.

Yepper:
> 
 I'm new to Ubuntu, installed it yesterday and it is great

In my humble opinion, the greatest Operating System the world has ever known. Usin's make it so.

There is that learning curve. Hang in there and make yours your own.

If this matter is concluded;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

