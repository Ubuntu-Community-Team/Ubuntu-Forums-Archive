---
title: "Help!! :( Loop Error."
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by kikeonline on 2008-05-25
OHHH MY GODD!!! I have 2 days with this problem please help me...I dont want to go back to Windows I want to be part of the UBuntu phylosophy, please help me!

First of all I cant Install Nothing because it tells me that I need to do this manually 'dpkg --configure -a' in the terminal... when I do that Iget this:

dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-06-0ubuntu1); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-plugin

And when I try to install the sun-java-bin $ sun-java-jre in the update manager it takes yeeearrrssssssss!!!!!!!!!!!!!!!!

I'm frustrated since i'm a noob.

thanks for you support.

---

### Post by molotov00 on 2008-05-25
> **kikeonline said:**
> 
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-06-0ubuntu1); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-plugin


And if you:

sudo apt-get install sun-java6-bin

What happens? Seems like installing java is the solution. 

Better yet, you may just skip dpkg altogether and use apt-get, which is the preferred installation method for packages. (if you know better, correct me)

---

### Post by kikeonline on 2008-05-25
OH MY GOD!!

I thougt I tried apt-get i'so newbe jajja


kike@ronald:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-06-0ubuntu1); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-plugin
kike@ronald:~$ sudo apt-get install sun-java6-bin
[sudo] password for kike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-06-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
kike@ronald:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
kike@ronald:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  sun-java6-fonts ttf-wqy-zenhei
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  sun-java6-jre
The following packages will be upgraded:
  sun-java6-bin
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/33.6MB of archives.
After this operation, 96.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 
dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
106137 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6-06-0ubuntu1_all.deb) ...
Preparing to replace sun-java6-bin 6-06-0ubuntu1 (using .../sun-java6-bin_6-06-0ubuntu1_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-bin ...
Setting up sun-java6-bin (6-06-0ubuntu1) ...

Setting up sun-java6-jre (6-06-0ubuntu1) ...

Setting up sun-java6-plugin (6-06-0ubuntu1) ...




ITS KNOW INSTALL???

---

### Post by Sef on 2008-05-25
Make sure that enter is highlighted.  Use the tab key to make sure it is.

---

### Post by kikeonline on 2008-05-25
kike@ronald:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of sun-java6-plugin:
sun-java6-plugin depends on sun-java6-bin (= 6-06-0ubuntu1); however:
Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
sun-java6-plugin
kike@ronald:~$ sudo apt-get install sun-java6-bin
[sudo] password for kike:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
sun-java6-bin: Depends: sun-java6-jre (= 6-06-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
kike@ronald:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
kike@ronald:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
sun-java6-bin sun-java6-jre
Suggested packages:
sun-java6-fonts ttf-wqy-zenhei
Recommended packages:
gsfonts-x11
The following NEW packages will be installed:
sun-java6-jre
The following packages will be upgraded:
sun-java6-bin
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/33.6MB of archives.
After this operation, 96.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ...
dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
106137 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6-06-0ubuntu1_all.deb) ...
Preparing to replace sun-java6-bin 6-06-0ubuntu1 (using .../sun-java6-bin_6-06-0ubuntu1_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-bin ...
Setting up sun-java6-bin (6-06-0ubuntu1) ...

Setting up sun-java6-jre (6-06-0ubuntu1) ...

Setting up sun-java6-plugin (6-06-0ubuntu1) ...




ITS INSTALL???  My Update Manager is all grey is not responding... if I restart eveything should work fine right?

---

### Post by molotov00 on 2008-05-25
Wait for a confirmed message before restarting. Better yet, don't restart.

If just the GUI is locking up, you can restart X (Ctrl+Alt+Backspace) (if I remember correctly).

If it really is locked up you can restart and try the apt-get command again. If the packages installed then apt-get will tell you that's the case. If it got half way, apt-get will resume. It's pretty smart in that regard.

M

---

### Post by kikeonline on 2008-05-26
[size="6"]**solved!**[/size]

---

