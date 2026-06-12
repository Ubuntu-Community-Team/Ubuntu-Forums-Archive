---
title: "[solved]How can I install ia32-libs in 14.04 LTS?"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by Jahidul_Hamid on 2014-08-25
I can't find ia32-libs in the repo. Where has it gone...?

---

### Post by slickymaster on 2014-08-25
[How to install ia32-libs in ubuntu 14.04 LTS]("http://stackoverflow.com/questions/23182765/how-to-install-ia32-libs-in-ubuntu-14-04-lts")

---

### Post by Jahidul_Hamid on 2014-08-25
The link is not working. It's taking forever....

---

### Post by slickymaster on 2014-08-25
> **Jahidul_Hamid said:**
> The link is not working. It's taking forever....

That's odd, it's working here. Can it be anything with your internet connection?

---

### Post by Jahidul_Hamid on 2014-08-25
No, internet's fine.. because all other pages are loading fine , but that page doesn't load at all..

---

### Post by slickymaster on 2014-08-25
Well if you don't manage to load that page I can copy/paste the process over here if you want me to.

---

### Post by Jahidul_Hamid on 2014-08-25
The page is working now... don't know what happened. And the problem has also been solved..thanks..
solution that worked for me:
> sudo -i
cd /etc/apt/sources.list.d
echo "deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) raring main restricted universe multiverse" >ia32-libs-raring.list
apt-get update
apt-get install ia32-libs
rm ia32-libs-raring.list

---

### Post by slickymaster on 2014-08-25
Glad you got it fixed.

Please, mark your thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), so other people searching the forums know that this thread provides a working solution for their problem.

---

