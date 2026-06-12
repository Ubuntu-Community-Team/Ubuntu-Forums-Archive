---
title: "Apt-Get hangs while trying to install anything"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by OzzyFreakDude on 2011-07-03
Hello all I am having an issue with my Ubuntu Lucid installation.  It has been working fine for a long time, and then all of a sudden in the past few days, it's been freezing as I try to install any packages.  In particular, it's happened with KlamAV and with Firestarter.  It gets up to the "Unpacking replacement menu ..." and just hangs indefinitely:   patrick@patrick-desktop:~$ sudo apt-get install firestarter Reading package lists... Done Building dependency tree        Reading state information... Done The following packages were automatically installed and are no longer required:   chromium-browser-inspector Use 'apt-get autoremove' to remove them. The following extra packages will be installed:   menu Suggested packages:   dhcp3-server The following NEW packages will be installed:   firestarter The following packages will be upgraded:   menu 1 upgraded, 1 newly installed, 0 to remove and 7 not upgraded. 1 not fully installed or removed. Need to get 0B/874kB of archives. After this operation, 4,108kB of additional disk space will be used. Do you want to continue [Y/n]? y (Reading database ...  dpkg: warning: files list file for package `menu' missing, assuming package has no files currently installed. (Reading database ... 250945 files and directories currently installed.) Preparing to replace menu 2.1.43ubuntu1 (using .../menu_2.1.43ubuntu1_amd64.deb) ... Unpacking replacement menu ...

---

### Post by dino99 on 2011-07-03
reading that stuff is a pain :( , so if you want help, dont discourage the braves.

clean your system:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

and check, into synaptic, that you dont have untrusted repo (like ppa)

sudo apt-get update
sudo apt-get install -f

---

### Post by OzzyFreakDude on 2011-07-03
sorry about that, somehow posting the thread removed all of my carriage returns :-/

in any case, I tried all of those commands, and autoremove and install -f don't work -  they also result in it hanging.

I'm getting a strange message about package 'menu': dpkg: warning: files list file for package `menu' missing, assuming package has no files currently installed.


Here's the terminal output (hopefully) conserving my carriage returns:
patrick@patrick-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  menu
The following packages will be REMOVED:
  chromium-browser-inspector
The following packages will be upgraded:
  menu
1 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/451kB of archives.
After this operation, 905kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `menu' missing, assuming package has no files currently installed.
(Reading database ... 250945 files and directories currently installed.)
Preparing to replace menu 2.1.43ubuntu1 (using .../menu_2.1.43ubuntu1_amd64.deb) ...
Unpacking replacement menu ...


EDIT:
it looks like something is wrong with my 'menu' package - so I tried to completely remove it in synaptic to install it again, and it tells me: E: menu: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.  But the 'mark for reinstallation' option is greyed out.

---

### Post by ExTruckie on 2011-07-03
> **OzzyFreakDude said:**
> sorry about that, somehow posting the thread removed all of my carriage returns :-/

in any case, I tried all of those commands, and autoremove and install -f don't work -  they also result in it hanging.

I'm getting a strange message about package 'menu': dpkg: warning: files list file for package `menu' missing, assuming package has no files currently installed.


Here's the terminal output (hopefully) conserving my carriage returns:
patrick@patrick-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  menu
The following packages will be REMOVED:
  chromium-browser-inspector
The following packages will be upgraded:
  menu
1 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/451kB of archives.
After this operation, 905kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `menu' missing, assuming package has no files currently installed.
(Reading database ... 250945 files and directories currently installed.)
Preparing to replace menu 2.1.43ubuntu1 (using .../menu_2.1.43ubuntu1_amd64.deb) ...
Unpacking replacement menu ...


EDIT:
it looks like something is wrong with my 'menu' package - so I tried to completely remove it in synaptic to install it again, and it tells me: E: menu: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.  But the 'mark for reinstallation' option is greyed out.


I had something similar happen to me recently where I could not install or uninstall anything either. I had tried most all the suggestions given me, but it got to a point it was obvious a reinstall was necessary.

---

