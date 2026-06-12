---
title: "Google Repositories causes stall in Update Manager"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by JPWhite on 2010-02-18
I installed Google Chrome on Xubuntu 9.10. Works great, using it right now. However it adds an additional software repository which causes the update manager process to stall for 3-4 minutes. I have tried apt-get update and apt-get upgrade from the command line. Stalls at the Google repository.

Is anyone else experiencing this problem or have a fix at hand? Short of unchecking the repository, I haven't found a fix online to this problem.

Repository added to software sources is
[http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable main

---

### Post by Bobber47 on 2010-02-19
Yes, I've been seeing the same delay of chrome package info from the google repository with 8.04.  Similarly, the update finishes without problems once the download of package info is complete.

---

### Post by JPWhite on 2010-02-20
> **Bobber47 said:**
> Yes, I've been seeing the same delay of chrome package info from the google repository with 8.04.  Similarly, the update finishes without problems once the download of package info is complete.

Thanks for feedback, I had begun to wonder if I was the only one experiencing this :-)

What really puzzles me is that there are very few posts complaining of this. :confused: I have 4 or 5 installs of Ubuntu/XUbuntu on various PC's and it is common to all of them. Clearly if you are experiencing the same with Hardy its not a Karmic issue.

Opera doesn't suffer from these type of update manager delays, one would think Google would have a better and faster infrastructure, especially since they are getting into Linux with Chrome OS.

---

### Post by altima on 2010-04-18
I have this same problem. it takes looong time to get this repository updated. did not find any solution on the net.

---

### Post by iLoveRuby on 2010-04-25
> **JPWhite said:**
> I installed Google Chrome on Xubuntu 9.10. Works great, using it right now. However it adds an additional software repository which causes the update manager process to stall for 3-4 minutes. I have tried apt-get update and apt-get upgrade from the command line. Stalls at the Google repository.

Is anyone else experiencing this problem or have a fix at hand? Short of unchecking the repository, I haven't found a fix online to this problem.

Repository added to software sources is
[http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable main

I believe this will fix the problem:

```
sudo touch /etc/apt/apt.conf.d/90google ; sudo echo "Acquire::http::Pipeline-Depth \"0\";" > /etc/apt/apt.conf.d/90google 
```

Restart your machine, and try to "sudo apt-get update" again.

---

### Post by twoshadetod on 2010-05-13
comes back with:
```
clay@jennascomputer:~$ sudo touch /etc/apt/apt.conf.d/90google ; sudo echo "Acquire::http::Pipeline-Depth \"0\";" > /etc/apt/apt.conf.d/90google
bash: /etc/apt/apt.conf.d/90google: Permission denied

```





> **iLoveRuby said:**
> I believe this will fix the problem:

```
sudo touch /etc/apt/apt.conf.d/90google ; sudo echo "Acquire::http::Pipeline-Depth \"0\";" > /etc/apt/apt.conf.d/90google 
```

Restart your machine, and try to "sudo apt-get update" again.

---

### Post by altima on 2010-05-25
the problem's solved by Google themselves.

---

