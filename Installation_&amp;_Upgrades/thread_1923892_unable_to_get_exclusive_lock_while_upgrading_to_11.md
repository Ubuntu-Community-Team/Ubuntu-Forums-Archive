---
title: "unable to get exclusive lock while upgrading to 11.10"
date: 2012-02-11
forum: Installation &amp; Upgrades
---

### Post by Mia_tech on 2012-02-11
I just ran the upgrade application to upgrade to 11.10; however, I got "unable to get exclusive lock while upgrading to 11.10." What does that mean? is this a bug or something?

Thanks

---

### Post by jerrrys on 2012-02-11
Do you have another package manager open?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=unable+to+get+exclusive+lock&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=unable+to+get+exclusive+lock&sa=Search&cof=FORID:9)

---

### Post by bluexrider on 2012-02-11
> **Mia_tech said:**
> I just ran the upgrade application to upgrade to 11.10; however, I got "unable to get exclusive lock while upgrading to 11.10." What does that mean? is this a bug or something?

Thanks
Usually means that two package managers are open at the same time. Automatic update running and using apt-get.

---

### Post by cortman on 2012-02-11
If you don't have any other visible package software running, you can fix by either logging out and back in, or running

```
ps -ef | grep apt
ps-ef | grep dpkg 
```

and killing all other currently running apt and dpkg processes, using 

```
kill -9 process_id
```

---

### Post by Mia_tech on 2012-02-12
no, no other package manager open! But upgrade worked....

---

### Post by raja.genupula on 2012-02-12
> **Mia_tech said:**
> no, no other package manager open! But upgrade worked....

you mean now , all fine ?

---

### Post by jerrrys on 2012-02-12
So cortman had the fix?

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

