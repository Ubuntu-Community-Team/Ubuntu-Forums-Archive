---
title: "ubuntu upgrade 12.04 to 14.04 broke my sa-compile"
date: 2015-08-12
forum: Installation &amp; Upgrades
---

### Post by Chen78 on 2015-08-12
i recently upgraded from 12.04 to 14.04 (usually i do clean install) had to upgrade because this machine had many custom configs
anyways

my problem started when gnome-session-fallback broke 
i started diging the internet and found many unusefull answers
so i decided to post a question here

when i try to upgrade now i get this:

```
root:~ # apt-get upgradeReading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up sa-compile (3.4.0-1ubuntu1) ...
Running sa-compile (may take a long time)
Can't exec "rm": No such file or directory at /usr/bin/sa-compile line 374, <$fh> line 1.
make: chmod: Command not found
make: *** [blib/lib/Mail/SpamAssassin/CompiledRegexps/.exists] Error 127
command 'make >>/tmp/.spamassassin22511kHb4gFtmp/log' failed: exit 2
dpkg: error processing package sa-compile (--configure):
 subprocess installed post-installation script returned error exit status 25
Errors were encountered while processing:
 sa-compile
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@:~ #
```


what i did so far is removing the SpamAssassin trying to re-install it
it always fails with this error

now before you tell me people already answered it please note that i looked in like 20 posts in the past 24 hours
and now i can't find any more ideas so i decided to come for help

any help given will be appreciated
thanks

---

### Post by dino99 on 2015-08-12
as you says: "lot of custom configs"
some may not respect the ubuntu default settings: pay attention to the rights allowed for the folder(s)/file(s) where these"custom configs" are located.

---

