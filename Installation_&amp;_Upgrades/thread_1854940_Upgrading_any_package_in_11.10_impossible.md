---
title: "Upgrading any package in 11.10 impossible"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by leveliv on 2011-10-05
Hi there,

I am running the beta or alpha whatever it is on my laptop of 11.10 
and I recently tried to upgrade my packages just to stay up to date and maybe fix a bug or two to make it stable. 

however when I try to use update manager I get an error saying I need to do a partial upgrade. When I do it stops when getting new packages It says the package system is broken and that I should run ```
sudo apt-get install -f
```

However when I run that I get this 

```
leveliv@leveliv-Satellite-L500:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc-bin libc6
Suggested packages:
  glibc-doc
The following NEW packages will be installed:
  libc-bin
The following packages will be upgraded:
  libc6
1 upgraded, 1 newly installed, 0 to remove and 444 not upgraded.
3 not fully installed or removed.
Need to get 994 kB/5,296 kB of archives.
After this operation, 3,420 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ oneiric/main libc-bin amd64 2.13-20ubuntu5 [994 kB]
Fetched 994 kB in 3s (266 kB/s)                        
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I have no idea how to fix it, Should I just re install from an .iso and try again? I haven't really got anything to lose from this point on, but I am trying to make myself learn more about linux rather than just reformat and refresh.

I could get a stable copy of 11.04 and try that but I always like being on the heels of Canonical just to see what they are coming up with next.

---

### Post by cottfcfan on 2011-10-05
What repos do you have enabled?

---

### Post by dino99 on 2011-10-05
use the "main" server via synaptic

---

### Post by leveliv on 2011-10-05
the only repos I have enabled are whatever is enabled by default I havent added or changed any. 

As for synaptic whenever I try to install it I get 

```
leveliv@leveliv-Satellite-L500:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-20ubuntu3)
 libc6-dev : Depends: libc6 (= 2.13-20ubuntu5) but 2.13-20ubuntu3 is to be installed
 libc6-i386 : Depends: libc6 (= 2.13-20ubuntu5) but 2.13-20ubuntu3 is to be installed
 synaptic : Depends: libapt-pkg4.11 (>= 0.8.16~exp5ubuntu12) but 0.8.16~exp5ubuntu11 is to be installed
            Depends: libept1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
Then whenever I do "sudo apt-get -f install" I get 
```
leveliv@leveliv-Satellite-L500:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-20ubuntu3)
 libc6-dev : Depends: libc6 (= 2.13-20ubuntu5) but 2.13-20ubuntu3 is to be installed
 libc6-i386 : Depends: libc6 (= 2.13-20ubuntu5) but 2.13-20ubuntu3 is to be installed
 synaptic : Depends: libapt-pkg4.11 (>= 0.8.16~exp5ubuntu12) but 0.8.16~exp5ubuntu11 is to be installed
            Depends: libept1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
leveliv@leveliv-Satellite-L500:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-20ubuntu3)
 libc6-dev : Depends: libc6 (= 2.13-20ubuntu5) but 2.13-20ubuntu3 is to be installed
 libc6-i386 : Depends: libc6 (= 2.13-20ubuntu5) but 2.13-20ubuntu3 is to be installed
 synaptic : Depends: libapt-pkg4.11 (>= 0.8.16~exp5ubuntu12) but 0.8.16~exp5ubuntu11 is to be installed
            Depends: libept1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
leveliv@leveliv-Satellite-L500:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc-bin libc6
Suggested packages:
  glibc-doc
The following NEW packages will be installed:
  libc-bin
The following packages will be upgraded:
  libc6
1 upgraded, 1 newly installed, 0 to remove and 444 not upgraded.
3 not fully installed or removed.
Need to get 0 B/5,296 kB of archives.
After this operation, 3,420 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
leveliv@leveliv-Satellite-L500:~$ 

```
And then a window from Ubuntu Software centre pops up and asks me to repair my packages, However when I try that same repair window just keeps popping up and asking the same thing. 
 If I want to repair my packages...but by that point its just an endless loop of that window popping up. 

I don't know if its myself that broke this machine or just an update gone back (my wifi likes to drop a lot) but even then it rolls back to the original state.

---

### Post by cottfcfan on 2011-10-05
Try editing your /etc/apt/sources.list,
and make sure the following are enabled or add them if they're not, then try again:
```
deb http://archive.ubuntu.com/ubuntu oneiric-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates main restricted
deb http://archive.ubuntu.com/ubuntu oneiric universe
deb-src http://archive.ubuntu.com/ubuntu oneiric universe
deb http://archive.ubuntu.com/ubuntu oneiric-updates universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates universe
deb http://archive.ubuntu.com/ubuntu oneiric multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric multiverse
deb http://archive.ubuntu.com/ubuntu oneiric-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates multiverse
deb http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb http://archive.ubuntu.com/ubuntu oneiric-security universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-security universe
deb http://archive.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-security multiverse

```

---

### Post by leveliv on 2011-10-07
I backed up and cleared out my old Sources.list and copied what you wrote down there, trying now will let people know if it works...Heres hoping.

---

### Post by Quackers on 2011-10-07
Never run a partial upgrade, it will often break something.
It is safer to use synaptic package manager to update packages. At least synaptic tells you waht it proposes to do and what will break if an update involves removal of packages.

---

### Post by bravecobra on 2011-10-15
I'm having the same problem here.

---

