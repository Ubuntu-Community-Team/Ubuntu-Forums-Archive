---
title: "Can Ubuntu 9.10 alpha be updated to beta/RC using update manager?"
date: 2009-05-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sumeshpremraj on 2009-05-16
Sorry if this question is available on FAQ/forum threads, I searched (but perhaps without the right keywords).

I downloaded Ubuntu Karmic alpha, and am wondering if and how I can upgrade it to the latest beta and final releases as they come out from within the update manager (I do not want to download a new iso every time there's a release)...

---

### Post by ninjapirate89 on 2009-05-16
Yes you should be able to upgrade right along with each new release.

---

### Post by xebian on 2009-05-16
> **sumeshpremraj said:**
> Sorry if this question is available on FAQ/forum threads, I searched (but perhaps without the right keywords).

I downloaded Ubuntu Karmic alpha, and am wondering if and how I can upgrade it to the latest beta and final releases as they come out from within the update manager (I do not want to download a new iso every time there's a release)...

Any installation can be updated/upgraded, and when you are done you have the latest version as of the time you did the update.  Update manager is just one of the many ways.

---

### Post by davideotape on 2009-05-17
> **sumeshpremraj said:**
> Sorry if this question is available on FAQ/forum threads, I searched (but perhaps without the right keywords).

I downloaded Ubuntu Karmic alpha, and am wondering if and how I can upgrade it to the latest beta and final releases as they come out from within the update manager (I do not want to download a new iso every time there's a release)...

See this thread: [http://ubuntuforums.org/showthread.php?t=1159389](http://ubuntuforums.org/showthread.php?t=1159389) :D

---

### Post by nhandler on 2009-05-17
Since you already have the Karmic repositories in /etc/apt/sources.list, simply do an 'apt-get update' to make sure that your computer is aware of new packages that have been uploaded. Then, just do a normal upgrade using any of the many methods available. This will ensure that all of your programs are up-to-date, and you will be running the beta/RC (once they are released)

---

### Post by twright on 2009-10-01
Whilst updating the system to the final release will just work, you might also want to look into the zsync command which will allow you to get the newer ISO but only need to download the changes from the previous ones.

---

