---
title: "Sub-process /usr/bin/dpkg returned an error code (100)"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by Sasa Sijak on 2008-03-13
I tried to install acroread but I didnt saw that my HD is full and the install break down in the middle of sudo apt-get install acroread process of downloading files from the net. And now when I fried some space and try to install anything I get this message. For example : 

dzigi@dzigi-laptop:~$ sudo apt-get install darkice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libtwolame0
The following NEW packages will be installed:
  darkice libtwolame0
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 174kB of archives.
After unpacking 549kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe libtwolame0 0.3.10-2 [57.5kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe darkice 0.18.1-1 [116kB]
Fetched 174kB in 7s (23.6kB/s)                                                 
**E: Sub-process /usr/bin/dpkg returned an error code (100)**
dzigi@dzigi-laptop:~$ 

And when I try to install acroread terminal says that it is allready installed :S
Please help I cant install or reinstall or uninstall anything :S Tried with synaptic managr also but with no sucess. I googled about this error but have found nothing ussefull.
Thanks in advance!

---

### Post by NorthernLights on 2008-03-13
I think you could reconfigure acroread to make sure it's in good state : 
```
sudo dpkg-reconfigure acroread
```

---

### Post by Sasa Sijak on 2008-03-13
```
dzigi@dzigi-laptop:~$ sudo dpkg-reconfigure acroread
Can't exec "dpkg": No such file or directory at /usr/sbin/dpkg-reconfigure line 77.
Use of uninitialized value in pattern match (m//) at /usr/sbin/dpkg-reconfigure line 78.
Use of uninitialized value in pattern match (m//) at /usr/sbin/dpkg-reconfigure line 79.
/usr/sbin/dpkg-reconfigure: acroread is not installed
dzigi@dzigi-laptop:~$ 
```

But I`m not worried just about acroreader, I can`t install ANYTHING else now :S

---

### Post by Sasa Sijak on 2008-03-13
For example : 

```
dzigi@dzigi-laptop:~$ sudo apt-get install **thunderbird**
[sudo] password for dzigi:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  thunderbird-gnome-support latex-xft-fonts
The following NEW packages will be installed:
  thunderbird
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 11.0MB of archives.
After unpacking 32.8MB of additional disk space will be used.
Get:1 http://security.ubuntu.com gutsy-security/main thunderbird 2.0.0.12+nobinonly-0ubuntu0.7.10.0 [11.0MB]
Fetched 11.0MB in 27s (395kB/s)                                                
**E: Sub-process /usr/bin/dpkg returned an error code (100)**
dzigi@dzigi-laptop:~$ 
```

That error pops up for every application!

---

