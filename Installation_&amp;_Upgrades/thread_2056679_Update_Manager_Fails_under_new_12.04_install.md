---
title: "Update Manager Fails under new 12.04 install"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by davidmoss1 on 2012-09-11
Installed 12.04 from CD burned with -i386.iso onto a HP netbook into a new partition.  Install went OK, GRUB seems to be working, but update manager returns with  'E:encountered a section with no package header, E;problem with merge list; /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'  Also Ubuntu Software Center fials to open.  Help!

---

### Post by chellrose on 2012-09-12
Try opening a terminal and running
```

sudo apt-get update
sudo apt-get upgrade

```

I've seen those error messages in two cases.
(1) The computer is not connected to the internet, or
(2) Two programs are trying to access the repositories at once (for example, opening Software Center and Update Manager at the same time, or trying to get updates in Update Manager while running sudo apt-get install (whatever) ).

---

### Post by jerrrys on 2012-09-12
If that doesnt work, open a terminal and try this:

sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

Found that here:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=update+manager+fails&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=update+manager+fails&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F")

---

### Post by davidmoss1 on 2012-09-12
Thanks to Sissy13 and jerrrys for the replys!  I am a newbie at this Linux stuff, and even after getting a couple of books at the local bookstore, I am still learning!

---

### Post by chellrose on 2012-09-13
I've been using Linux for 7 years now, and I'm still learning too.

Did you get it working?

---

