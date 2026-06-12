---
title: "Unable to install Aptitude package: ubuntu 22.04"
date: 2022-10-13
forum: Installation &amp; Upgrades
---

### Post by samarth51 on 2022-10-13
Hi,

I am unable to install "Aptitude" package for my Ubuntu version 22.04.

Attached the terminal with command. 
any suggestions would be highly appreciated.

Thanks
Samarth

---

### Post by tea for one on 2022-10-13
```
edited@edited:~$ apt policy aptitude
aptitude:
  Installed: (none)
  Candidate: 0.8.13-3ubuntu1
  Version table:
     0.8.13-3ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
edited@edited:~$ 
```
aptitude is in the universe repository.
Do you have this repo enabled in your software sources?

---

### Post by samarth51 on 2022-10-13
Hi,
thanks. I realized that universe repository was not enabled.
I enabled the repository and successfully installed the aptitude.

Cheers

---

### Post by tea for one on 2022-10-13
In order to help other forum members/searchers, it is a nice gesture to mark the thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

