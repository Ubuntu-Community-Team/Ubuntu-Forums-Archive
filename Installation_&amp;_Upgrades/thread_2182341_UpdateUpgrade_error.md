---
title: "Update/Upgrade error"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by crj54 on 2013-10-20
Part way through  upgrading from 13.04 to 13.10 the process ground to a halt with an error  message. Now on retrying by going to 'Check for updates' or 'Sudo Apt-get update' via the terminal I get the  following:


  Failed to load the package list
  This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.
  E:Encountered a section with no Package: header, E:Problem with  MergeList  /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_universe_i18n_Translation-en%%5fGB,  E:The package lists or status file could not be parsed or opened.

In the terminal (just showing the end of the listing):


Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-backports/universe Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/main Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/multiverse Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-security/universe Translation-en_GB
Fetched 63.1 kB in 45s (1,378 B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_universe_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.



  Problem reported but my question is, "what can I do now?; Do I have  to do a fresh install?; if so will settings etc. in my Home folder (on  its own partition) be saved?"
  13.04 still seems to be working perfectly, while upgrading I had a  terrible internet connection varying between 'dead slow' and 'dead  stop', not sure if that caused the problem.

---

### Post by carl4926 on 2013-10-21
If /home is separate then absolutely your settings will be saved. Just make sure it's not formatted. You still have to set the mount point for it as /home
And use the same username as you had.
AFAIK 13.10 should also offer users with no separate home the ability to keep the /home files safe.

---

### Post by Bashing-om on 2013-10-21
crj54; Hi !

Let's say your control files are in an inconsistent state;
try this;
Terminal codes:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

``` "update" will rebuild the control files.

Then see where you are, perhaps have to (re)start the upgrade to version 13.10 ?

[INDENT][INDENT]maybe yes now, maybe not so yes
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-10-21
crj54; Hi !

Let's say your control files are in an inconsistent state;
try this;
Terminal codes:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

``` "update" will rebuild the control files.

Then see where you are, perhaps have to (re)start the upgrade to version 13.10 ?

[INDENT][INDENT]maybe yes now, maybe not so yes
[/INDENT][/INDENT]

---

