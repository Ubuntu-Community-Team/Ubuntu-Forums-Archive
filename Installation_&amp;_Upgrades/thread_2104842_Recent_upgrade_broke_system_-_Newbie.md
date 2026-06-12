---
title: "Recent upgrade broke system - Newbie"
date: 2013-01-14
forum: Installation &amp; Upgrades
---

### Post by MatadorMac on 2013-01-14
Good day.  A recent Ubuntu upgrade to the newest version broke my otherwise stable system.  It seems that I have somehow deleted(?) a program needed to work with "tar" files.

I have run "sudo apt-get clean" and " sudo apt-get update && sudo apt-get dist-upgrade" 

The process downloads all files but during installation ends with the following error:

dpkg: warning: 'tar' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

I have been having this problem for a month now and cannot resolve it with my level of understanding.  I would appreciate any and all help.

Best

Mark

---

### Post by ibjsb4 on 2013-01-14
Have you tried ..

```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

### Post by MatadorMac on 2013-01-15
> **ibjsb4 said:**
> Have you tried ..

```
sudo dpkg --configure -a && sudo apt-get -f install
```

Hi.  Thanks for replying.  I just tried your suggestion with these results:

dpkg: warning: 'tar' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
markmackenzie@mark-linux-desktop:/var/lib/apt$ ^C

I am a newbie in Linux even though I have been running Ubuntu in a dual boot on my XP box for several years.

Any more thoughts?

Mark

---

### Post by ibjsb4 on 2013-01-15
Ok, looks like your tar package is broke and needs to be reinstalled.  But here's the catch22.

When you download a package, it comes in .tar format.  So in your case you need tar to download tar.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=warning%3A+%27tar%27+not+found+in+PATH+or+not+executable&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=warning%3A+%27tar%27+not+found+in+PATH+or+not+executable&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F")

The option I know of is to download it from the live CD.  I would suggest opening a new thread and ask for help with this, if you need it.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+package+from+live+cd&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+package+from+live+cd&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by MatadorMac on 2013-01-19
Alright, problem solved, now.  However, it took a reinstall/repair using 12.10 Ubuntu.  After selecting the install system option another option comes up which is to reinstall operating system but keep applications and files.  This actually worked and preserved my email which is what I was most concerned about.


There were some programs needing to be reinstalled but I am not sure that this wasn't caused by my broken operating system which I have been trying to fix for nearly 2 months.

I am now a happy camper.

Best

MatadorMac ):P

---

### Post by ibjsb4 on 2013-01-19
Congratulations  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

