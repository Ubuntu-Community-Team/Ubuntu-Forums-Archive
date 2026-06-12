---
title: "uprade broke kate"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by tamman2000 on 2008-02-11
I came into my office this morning to find my machine telling me that there are updates waiting for me.  So I start the update (a whole bunch of kde libs and utils) and go on about my day.  A couple of minutes later (I am not sure what point of the update was ongoing, only that the dl was finished) my machine freezes hard (no inputs accepted at all)  so I hit the reset button...

everything seems fine until I go to edit a file, and kate doesn't open.  try it from a bash shell, and I get that kate has a bus error when I try to launch.  apt-get upgrade, upgrades nothing (does that mean that my update this morning took?) apt-get reinstall kate doesn't fix the problem...

I use kate a lot, I need this to work...  Help, please...

---

### Post by Pumalite on 2008-02-11
Run:
sudo apt-get install -f
Post the output.

---

### Post by tamman2000 on 2008-02-11
$ sudo apt-get install -f
[sudo] password for dailey:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nspluginwrapper libntfs-3g12
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I have also noticed that the problem is effecting kwrite as well (not surprising I guess).

---

### Post by Pumalite on 2008-02-11
Run:
sudo apt-get autoremove
And then see if you can use apt-get to install anything.
If so, you might be able to resume your update.

---

### Post by tamman2000 on 2008-02-11
Still no love...

Tried it...  doesn't look like it continued any install...

I am not certain that the install was incomplete at the time of my freeze this morning either...

---

### Post by Pumalite on 2008-02-11
What's the output of:
sudo apt-get update
sudo apt-get upgrade

---

### Post by tamman2000 on 2008-02-11
$ sudo apt-get update
[sudo] password for dailey:
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages
Fetched 12B in 1s (9B/s)
Reading package lists... Done
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Pumalite on 2008-02-11
Try:
sudo aptitude install soundkonverter
Tell me what happens.

---

### Post by tamman2000 on 2008-02-11
$ sudo aptitude install soundkonverter
[sudo] password for dailey:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  flac libqt0-ruby1.8
The following NEW packages will be installed:
  flac libqt0-ruby1.8 soundkonverter
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1037kB of archives. After unpacking 4125kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main flac 1.1.4-3ubuntu1.1 [171kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe libqt0-ruby1.8 4:3.5.7-1ubuntu4 [339kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe soundkonverter 0.3.6-0ubuntu1 [527kB]
Fetched 1037kB in 4s (253kB/s)
Selecting previously deselected package flac.
(Reading database ... 157333 files and directories currently installed.)
Unpacking flac (from .../flac_1.1.4-3ubuntu1.1_amd64.deb) ...
Selecting previously deselected package libqt0-ruby1.8.
Unpacking libqt0-ruby1.8 (from .../libqt0-ruby1.8_4%3a3.5.7-1ubuntu4_amd64.deb) ...
Selecting previously deselected package soundkonverter.
Unpacking soundkonverter (from .../soundkonverter_0.3.6-0ubuntu1_amd64.deb) ...
Setting up flac (1.1.4-3ubuntu1.1) ...
Setting up libqt0-ruby1.8 (4:3.5.7-1ubuntu4) ...
Setting up soundkonverter (0.3.6-0ubuntu1) ...

Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

---

### Post by Pumalite on 2008-02-11
Your apt-get is fine. You should be able to update your system whenever updates are available. Should be able to reinstall kate or whatever else you want.

---

### Post by tamman2000 on 2008-02-11
If that is the case, what is this?

dailey@Quimby:~/$ sudo apt-get --reinstall install kate
[sudo] password for dailey:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/843kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 157677 files and directories currently installed.)
Preparing to replace kate 4:3.5.8-0ubuntu2.2 (using .../kate_4%3a3.5.8-0ubuntu2.2_amd64.deb) ...
Unpacking replacement kate ...
Setting up kate (4:3.5.8-0ubuntu2.2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: file /usr/lib/libkorganizer.so.1 is truncated

/sbin/ldconfig.real: file /usr/lib/libkorganizer.so.1.0.0 is truncated

/sbin/ldconfig.real: file /usr/lib/libgwsoap.so.0.0.0 is truncated

/sbin/ldconfig.real: file /usr/lib/libgwsoap.so.0 is truncated

dailey@Quimby:~/$ kate
Bus error (core dumped)
dailey@Quimby:~/$

---

### Post by Pumalite on 2008-02-11
I'm in my Apple laptop right now. I'll get back to you. If somebody else can help in the meantime, he is more than welcome.

---

### Post by tamman2000 on 2008-02-11
Even if you don't ultimately resolve this, I want to thank you for the time you have put into helping me.

---

### Post by Pumalite on 2008-02-11
I tried to resolve your problem and I failed. Maybe you need to reinstall. I hope somebody comes up with a better answer. I'm sorry.

---

### Post by tamman2000 on 2008-02-11
What does apt-get reinstall do?  it only reinstalls the package in question, not things it depends on, right?

since kate, and kwrite both don't work (I haven't found any other apps that don't work) could it be that some common dependency of these two apps is borked?  would apt-get reinstall take care of that?

How can I figure out what dependencies a package has?

---

### Post by tamman2000 on 2008-02-12
Resolved!

One of my co-corkers fixed it when I wasn't around, so I don't have all the answers about what he did, but he said that korganizer and kdepim-kresources were messed up...

---

### Post by Pumalite on 2008-02-12
Congrats. I learned something today.

---

