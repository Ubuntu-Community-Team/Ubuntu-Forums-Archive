---
title: "Not installing any software"
date: 2012-12-03
forum: Installation &amp; Upgrades
---

### Post by richmusa1 on 2012-12-03
I installed some software on my machine and since then it refuses to install other here is the error I get below,

 apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 git-core : Depends: liberror-perl but it is not going to be installed
            Recommends: curl but it is not going to be installed
 libdigest-sha1-perl : Depends: perlapi-5.10.1 but it is not installable
 libperl5.14 : Depends: perl-base (= 5.14.2-6ubuntu2.1) but 5.14.2-13 is to be installed
 perl : Depends: perl-base (= 5.14.2-6ubuntu2.1) but 5.14.2-13 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by TheFu on 2012-12-03
Try
$ sudo apt-get -f install

How did that work out?

---

### Post by richmusa1 on 2012-12-05
I tried that it did not work.

---

