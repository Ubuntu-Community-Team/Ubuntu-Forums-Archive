---
title: "responding to one package of many"
date: 2018-05-02
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2018-05-02
i am installing many (2000+) packages in a script running in a detached screen session (a nice form of background).  one of the packages part way through clears the screen and displays a warning with an <OK> prompt and expects me to type in carriage return to approve installing it.  i do want it to be installed.  so i have attached to that screen session, read the warning, and pressed carriage return and the whole install resumes.  i ran it with a carriage return piped in to its STDIN but that did not work.  the piped carriage return might have been read in by something along the way.

**is there a way to have this prompt skipped?**  i see no option for apt-get that might do this (i am already using -y on it).

---

### Post by Xian on 2018-05-02
Try reconfiguring the behavior of debconf:

```
$ sudo dpkg-reconfigure debconf
```

Then choose Noninteractive from the list of options.

---

### Post by Skaperen on 2018-05-03
> **Xian said:**
> Try reconfiguring the behavior of debconf:

```
$ sudo dpkg-reconfigure debconf
```

Then choose Noninteractive from the list of options.

**is there a way to do this in a script?**  until all the packages are installed, the only access i have is sending a script to be run.  i don't have ssh access until after everything is installed.  is this stored in a config file i can have a bash script update maybe with tools like awk and sed?

---

