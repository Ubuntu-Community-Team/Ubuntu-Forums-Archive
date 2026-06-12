---
title: "Firefox not upgraded after upgrading from 6.06 to 6.10"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Christian Hansen on 2006-10-30
I upgraded from 6.06 to 6.10 but my firefox browser is still version 1.5.0.1. Wasent the upgrade suppose to include Firefox 2.0 ?

Regards

Christian

---

### Post by David Valentine on 2006-10-30
I have the same problem.  And synaptic was insisting that firefox 2.0 was installed, which firefox "help/about" contradicted.  Here is what I did, which is a cautionary tale of what NOT to do.

My reasoning was that if I uninstalled firefox using synaptic and deleted all firefox folders I could find, then I could reinstall firefox using synaptic and know that I have the current version.  So that's what I did.  That forced me to also uninstall about 8 other packages that depended on firefox.  Now, my attempts to reinstall firefox using synaptic are failing.  At first, synaptic would report an error that firefox was trying to write to j2re1.4 which conflicted with an existing file, so I uninstalled that.  Then it said the same thing about sun-java-5, so I tried to uninstall that, too, but that failed.  I tried again to install firefox, and this time synaptic reported success, but firefox won't execute (can't find file).

So, because of all this, I'm about to start from scratch and do a clean install of edgy.  That is, unless someone can enlighten me about how to get firefox installed using apt.

---

### Post by drew_t on 2006-10-30
I'm having the same problem.

---

### Post by drew_t on 2006-10-31
There seem to be other people having this problem, too -  see [http://ubuntuforums.org/showthread.php?t=289471&highlight=firefox](http://ubuntuforums.org/showthread.php?t=289471&highlight=firefox) ; [http://ubuntuforums.org/showthread.php?t=284317&page=4&highlight=firefox](http://ubuntuforums.org/showthread.php?t=284317&page=4&highlight=firefox) (message #34); [http://ubuntuforums.org/showthread.php?t=283965&page=2&highlight=firefox](http://ubuntuforums.org/showthread.php?t=283965&page=2&highlight=firefox) (message #19) .

Anyone have any idea what's going on here?  Synaptic indicates that FF 2.0 is already installed, but when FF is actually started, the old 1.5 one is what comes up.  Reinstalling FF2.0 in Synaptic doesn't seem to have any effect.

---

### Post by Christian Hansen on 2006-11-01
Exactly my problem. Havent found any solution yet...Package manager also sais FF 2.0 here, but its 1.5 I have...

---

### Post by Joe_CoT on 2006-11-01
Firstly, make sure you've followed the [edgy upgrade procedure]("https://help.ubuntu.com/community/EdgyUpgrades"). If the problem persists, continue.

I had a similar problem on my desktop. my /usr/bin/firefox was a symlink to /opt/firefox/firefox, which was 1.5
2.0 Firefox was installed, but was installed to /usr/lib/firefox
Try
```

cd /usr/bin
ls -la firefox
```

to see what firefox points to. If it points to /opt/firefox:

```

sudo rm firefox
sudo ln -s /usr/lib/firefox/firefox firefox

```

Should do it. I'm on my laptop currently, and had no such problem. I think it might've been caused by using the Edgy RC, but I can't say for sure. Then again, this might not even be the issue at all, as I've changed so many things on my Desktop I don't even know what's standard anymore :-k

---

### Post by drew_t on 2006-11-02
Thanks, Joe.  That did the trick.

---

### Post by Joe_CoT on 2006-11-02
> Thanks, Joe. That did the trick.

No problem. Looking at other posts, it looks like this only happens with people who installed firefox manually (which I probably did at *some* point). So this isn't really a bug in Edgy as much as something we just noticed because of the upgrade.

---

### Post by Christian Hansen on 2006-11-03
Thanks Joe, now it works. 

I ugraded to 6.10 as was recommended, ie. using 

gksu "update-manager -c"

But still had the problem.

---

### Post by David Valentine on 2006-11-03
One thing I noticed was that Swiftfox *was* upgraded to 2.0.  Is there some sort of conflict during the upgrade that lets one be upgraded but not the other?

---

### Post by dief-eh? on 2006-11-14
> **Joe_CoT said:**
> No problem. Looking at other posts, it looks like this only happens with people who installed firefox manually (which I probably did at *some* point). So this isn't really a bug in Edgy as much as something we just noticed because of the upgrade.
hello,
i'm appreciating this thread, since i have also recently noticed that (help/about) lists my firefox version as 1.5.0.4, despite System/about Ubuntu saying i have 6.10 (edgy). gah. as often happens, the thread advice differs from the circumstances on my computer just enough to make me nervous, & ask for someone more experienced to take a look:

ls -la /usr/bin | less ...produces:
...
lrwxrwxrwx  1 root   root         20 2006-03-26 16:02 firefox -> /opt/firefox/firefox
lrwxrwxrwx  1 root   root         22 2006-10-27 20:41 firefox.ubuntu -> ../lib/firefox/firefox
...

If it points to /opt/firefox: [and it does]

cd /usr/bin
sudo rm firefox
sudo ln -s /usr/lib/firefox/firefox firefox

...but what's firefox.ubuntu? an automatix relic? 

fyi, btw, :c), i did use aysiyu's script to upgrade from 1.5.0.4 to 2.0 back when i was still using dapper.

---

### Post by dief-eh? on 2006-11-14
hello
not really a reply, but wanted to add that i subsequently thought "what the hell! go for it..." and i'm happy to report that help:about now lists firefox as version 2.0.

thanks to everyone who posted to the thread...

---

