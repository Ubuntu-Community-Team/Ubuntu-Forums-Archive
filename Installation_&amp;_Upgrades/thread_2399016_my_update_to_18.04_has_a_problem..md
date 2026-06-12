---
title: "my update to 18.04 has a problem."
date: 2018-08-20
forum: Installation &amp; Upgrades
---

### Post by andrew_s4 on 2018-08-20
after updating to 18.04 I get an error message: 'Error: BrokenCount >0'

I've run apt-get install -f and get:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

and this is as far as I get.

When running updates I get: 'The Package system is broken.' and nothing further happens of course.


I am not a competent Ubuntu user and don't really unterstand much of what I'm doing in this field, and so would appreciate some help in a user friendly language please! :p 
Thanks
Andrew

---

### Post by andrew_s4 on 2018-08-20
hmm, what does the following require from me now?

The following packages have unmet dependencies:
 libsnmp30:i386 : Depends: libperl5.26:i386 (>= 5.26.0~rc1) but it is not installed

And how do I go about resolving it!

---

### Post by Bashing-om on 2018-08-20
andrew_s4; Humm ..

> 
libsnmp30:i386 : Depends: libperl5.26:i386 (>= 5.26.0~rc1) but it is not installed


But but but ... that ^ is a old version, per:
> 
sysop@x1804mini:~$ apt policy libsnmp30:i386
libsnmp30:i386:
  Installed: (none)
  Candidate: 5.7.3+dfsg-1.8ubuntu3
  Version table:
     5.7.3+dfsg-1.8ubuntu3 500
        500 [http://mirror.steadfast.net/ubuntu](http://mirror.steadfast.net/ubuntu) bionic/main i386 Packages
sysop@x1804mini:~$


Let's see if we can determine what is going on here; post back your result from the terminal commands:
```

apt policy libsnmp30:i386
apt depends libsnmp30:i386
apt rdepends libsnmp30:i386

```

And make sure you are as updated as you can be under the circumstances:
```

sudo apt update
sudo apt upgrade

```

[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

---

### Post by andrew_s4 on 2018-08-24
Hi, thanks for your reply. It takes a while as I'm not around as much as I need to be. Anyway, I've run the terminal commands and this is what came back:

sav@sav-desktop:~$ apt policy libsnmp30:i386
libsnmp30:i386:
  Installed: 5.7.3+dfsg-1.8ubuntu3
  Candidate: 5.7.3+dfsg-1.8ubuntu3
  Version table:
 *** 5.7.3+dfsg-1.8ubuntu3 500
        500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic/main i386 Packages
        100 /var/lib/dpkg/status
sav@sav-desktop:~$ apt depends libsnmp30:i386
libsnmp30:i386
  Depends: libc6:i386 (>= 2.17)
  Depends: libpci3:i386 (>= 1:3.5.2-1)
  Depends: libperl5.26:i386 (>= 5.26.0~rc1)
  Depends: libsensors4:i386 (>= 1:3.0.0)
  Depends: libssl1.1:i386 (>= 1.1.0)
  Depends: libwrap0:i386 (>= 7.6-4~)
  Depends: <libsnmp-base:i386>
    libsnmp-base
  Replaces: <libsnmp-base:i386> (<< 5.4.2.1~dfsg-4)
  Replaces: snmp:i386 (<< 5.4.3~dfsg-1)
sav@sav-desktop:~$ apt rdepends libsnmp30:i386

I haven't the slightest idea what this all means... 
I've also made sure everything was updated and upgraded as per apt update etc.
Thanks for your help

---

### Post by Bashing-om on 2018-08-24
andrew_s4; Well,

Looks reasonable.

Try:
```

sudo apt install libperl5.26:i386

```

[INDENT][INDENT]Maybe Yes
[/INDENT][/INDENT]

---

### Post by andrew_s4 on 2018-08-25
Tried that, this came back:

sav@sav-desktop:~$ sudo apt install libperl5.26:i386
[sudo] password for sav: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libperl5.26 : Breaks: libperl5.26:i386 (!= 5.26.1-6ubuntu0.1) but 5.26.1-6ubuntu0.2 is to be installed
 libperl5.26:i386 : Depends: perl-modules-5.26:i386 (>= 5.26.1-6ubuntu0.2)
                    Breaks: libperl5.26 (!= 5.26.1-6ubuntu0.2) but 5.26.1-6ubuntu0.1 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
sav@sav-desktop:~$ apt --fix-broken install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
sav@sav-desktop:~$ 

I'm lost in space!

---

### Post by LHammonds on 2018-08-25
Problem = "permission denied"

You ran:

```
apt --fix-broken install
```

To correct the permission denied problem, put "sudo" before the command to "run as root"

```
sudo apt --fix-broken install
```

Anytime you run a command and it says "permission denied, are you root" then it probably means you need to add "sudo" to the front of the command.

LHammonds

---

### Post by andrew_s4 on 2018-08-25
Thank you both very much, that has fixed the problem.

---

### Post by Bashing-om on 2018-08-25
andrew_s4; Great !

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

