---
title: "Cannot connect to &quot;http://archive.cononical.com/&quot; for updates."
date: 2013-08-15
forum: Installation &amp; Upgrades
---

### Post by timelord04 on 2013-08-15
I'm new to Ubuntu and Linux in general; so, please be kind and patient.  I am on Ubuntu 12.0.4 on the current Linux Kernel.  I've been getting routine updates until today, 8-15-2013.  Suddenly a red triangle with a red exclamation point appeared on the top task/application bar.  When I clicked on it it stated that Update Manager could NOT connect to "http://archive.cononical.com/" for updates.

I found how to change the Server that Update Manager connects to; and, changed it to another US Server - then tried checking for updates again.  The same error occurred.

If I cannot connect to "archive.cononical.com" how am I supposed to obtain updates to Linux?  Please help; many thanks in advance.  (Beware, I am primarily a Windows 7 Home Premium user.)  My Linux system has been running for about two weeks in its present state and just acted up like this.


Scott
aka:  TimeLord04

---

### Post by ibjsb4 on 2013-08-15
Its not:

[http://archive.c](http://archive.c)[COLOR=#ff0000]**o**[/COLOR]nonical.com/

but

[http://archive.c](http://archive.c)[COLOR=#ff0000]**a**[/COLOR]nonical.com/

[Open at terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
cat /etc/apt/sources.list
```

And please post the output :)

---

### Post by timelord04 on 2013-08-15
Here it is:

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise main restricted
deb-src [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise-updates main restricted
deb-src [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise universe
deb-src [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise universe
deb [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise-updates universe
deb-src [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise multiverse
deb-src [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise multiverse
deb [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise-updates multiverse
deb-src [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise-backports main restricted universe multiverse

deb [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise-security main restricted
deb-src [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise-security main restricted
deb [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise-security universe
deb-src [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise-security universe
deb [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise-security multiverse
deb-src [http://cosmos.cites.illinois.edu/pub/ubuntu/](http://cosmos.cites.illinois.edu/pub/ubuntu/) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.cononical.com/](http://archive.cononical.com/) precise partner
deb-src [http://archive.cononical.com/](http://archive.cononical.com/) precise partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

---

### Post by ibjsb4 on 2013-08-15
> deb [http://archive.cononical.com/](http://archive.cononical.com/) precise partner
deb-src [http://archive.cononical.com/](http://archive.cononical.com/) precise partner

You need to edit these two lines and change that 'o' to an 'a' (as in canonical).

So again open a terminal and enter:

```
gksudo gedit /ect/apt/sources.list
```

And correct the spelling.  But before you do that, lets create a backup copy.  In terminal:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

Ok, go for it :)

---

### Post by deadflowr on 2013-08-15
comment out (#) the lines with cononical at the end of the sources.list.
You can do so either using gedit
```
gksu gedit /etc/apt/sources.list
```
or with terminal editors such as nano
```
sudo nano /etc/apt/sources.list
```

Edit: Yeah follow ibjsb4's advice and backup, but there's no need to change the line, just  add a # to the line.
You already have another line in the file for the partner repos.

---

### Post by ibjsb4 on 2013-08-15
Yep, I be blind :)  Thanks deadflowr

Just put a hash mark (#) in front of those two lines.

---

### Post by timelord04 on 2013-08-15
To both of you; thank you very much.  "gedit" worked fine.  I made the changes and saved them.  Then reran Update Manager, and this time there were no errors.  It said "Software is up to date."


Scott
aka:  TimeLord04

---

### Post by ibjsb4 on 2013-08-15
And welcome to the forums. Don't forget

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

