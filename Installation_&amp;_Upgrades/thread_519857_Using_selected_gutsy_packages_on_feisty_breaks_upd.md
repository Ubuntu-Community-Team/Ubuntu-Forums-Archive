---
title: "Using selected gutsy packages on feisty breaks updates"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by StackTrayce on 2007-08-07
We have a few developer workstations running feisty but need the ant 1.7.0 package from gutsy. I looked through the wiki and read about apt pinning in various documents and set up my sources.list to include the gutsy main repo:
```
deb http://us.archive.ubuntu.com/ubuntu gutsy main
```

I then set up apt pinning in /etc/apt/preferences to favor feisty over gutsy:
```
# first two stanzas make sure feisty (current) packages have higher
# priority than gutsy (next release) packages
Package: *
Pin: release a=feisty
Pin-Priority: 700

Package: *
Pin: release a=gutsy
Pin-Priority: 600

# Pin our ant release to exactly version 1.7.0, even tho this comes from gutsy
Package: ant
Pin: version 1.7.0*
Pin-Priority: 1001
```

I expected an apt-get update/upgrade would upgrade my ant, but it would not (as shown w/ -s), so I did an apt-get install -t gutsy ant and this worked for ant but I also have a few other gutsy packages (such as openoffice and apport, etc) which got pulled down for some reason. At this point everything worked fine and I had ant 1.7.0.

But recently there was a firefox update and an apt-get update/upgrade did not upgrade my firefox. A dpkg-query -W firefox shows version 2.0.0.5+1-0ubuntu1.

Does anyone have any suggestions as to how to get my machine properly pulling updates from feisty again while still having ant 1.7.0? Any other advice? Some people on IRC seem to think mixing gutsy and feisty packages is a horrible idea, but I found a wiki link showing how to do it so I am a bit confused.

Thanks in advance!

---

### Post by krazytekn0 on 2007-08-08
I think (I am no expert though!) that you ought to uninstall ant 1.7.0 through apt and basically undo what you did up there. Then download the ant binary package from ant.apache.org ...
[http://ftp.wayne.edu/apache/ant/binaries/apache-ant-1.7.0-bin.tar.bz2](http://ftp.wayne.edu/apache/ant/binaries/apache-ant-1.7.0-bin.tar.bz2)

Then make yourself some launchers and run the sucker. 

Seems like the easiest way to me.

of course you have to extract the files also

---

