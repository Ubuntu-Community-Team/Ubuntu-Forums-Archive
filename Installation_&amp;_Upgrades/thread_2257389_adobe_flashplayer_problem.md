---
title: "adobe flashplayer problem"
date: 2014-12-19
forum: Installation &amp; Upgrades
---

### Post by HR70s on 2014-12-19
I have 14.04 lts. For some reason now I can't stream. I wanted to watch a rerun on CBS.com and at the top of the CBS page I get: " firefox has prevented an outdated adobe flash
from running on [www.cbs.com](www.cbs.com) To the right of that I have 2 boxes keep blocking and allow. If I allow I can watch the videos. I went to the terminal and ran for updates but it comes
up I already have the latest version. Any idea what's going on! Thanks HR

---

### Post by Bucky Ball on 2014-12-19
I did a full:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... and it fixed the problem for me. ;)

---

### Post by Impavidus on 2014-12-19
If you installed flash the proper way an upgrade should give you version 11.2.202.425.

---

### Post by HR70s on 2014-12-20
Hey thanks.  I'll give it a shot Sunday. Working nights I live like a vampire ha ha

---

### Post by HR70s on 2014-12-21
I tried 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade as was suggested but it didn't help. When I check it says I have firefox ver. 30.0+build1-0ubuntu that's
exactly the way it's written. Any other ideas? Thanks.

---

### Post by Impavidus on 2014-12-21
That's an outdated version too. We should have Firefox 34.

Did **sudo apt-get update** and **sudo apt-get upgrade** give any errors or warnings? Please show us the full output.

---

### Post by HR70s on 2014-12-22
Solved! Downloaded Google Chrome. Now videos play fine.

---

### Post by Bucky Ball on 2014-12-22
Good news. Please mark the thread as solved (see second link in my signature). 

It is odd that you have an out-of-date Firefox, though. Would have been good to see the full output of your update/upgrade, as suggested (and use [code] tags for code, please). Getting that up to date may also have worked. ;)

Good luck.

---

### Post by monkeybrain20122 on 2014-12-22
Something is wrong with your Firefox or flash plugin. It works for me on Firefox 34.

---

### Post by Bucky Ball on 2014-12-22
> **monkeybrain20122 said:**
> Something is wrong with your Firefox or flash plugin. It works for me on Firefox 34.

This is what I'm thinking. :-k

If you want to fix this, perhaps post the full output of your update/upgrade commands in [code] tags. If you haven't got Firefox 34 after an update/upgrade, then something is wrong.

As I mentioned in my first post, I was getting the same error until I did an update/upgrade.

---

### Post by PopsTheSailor on 2015-07-18
I know this is an old thread but WOW so helpful!!!

I'm on Firefox 39 and my flash wasn't working. I started going down the manual path of downloading latest version, uncompressing..... Then thought I would do a search in the forums. Manual process was complicated for me but I ran across this thread. 

I did:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

And it fixed my problem. I probably didn't need to but it recommend I run

sudo apt-get autoremove

So I did that too. Looks like it cleaned things up.

I'm posting here to keep this thread a bit more active in case others have the same issues with newer versions of FF

Thanks Bucky Ball for the directions!!!

---

### Post by Bucky Ball on 2015-07-18
> **PopsTheSailor said:**
> 

Thanks Bucky Ball for the directions!!!

The pleasure is all mine. :)

---

