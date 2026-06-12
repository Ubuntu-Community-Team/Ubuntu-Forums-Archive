---
title: "[dapper] apt-get hangs forever trying to download headers"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by bspeakmon on 2007-03-09
I was having problems with Edgy on my shiny new Dell Latitude d620, and it was suggested that I try using dapper.

During install last night, apt for some reason had trouble connecting to the repositories to download updated package information. I figured out how to kill the http process spawned by apt, and the install completed successfully. Everything works fine, including networking (I'm posting from the laptop).

But now that the system has installed, apt-get (and aptitude) seem to hang forever on update. I get the update notification on my desktop that new packages are available for download, but when synaptic/apt-get/whatever tries to fetch them, all I get is:

```
prompt$ sudo apt-get update
0% [Waiting for headers]
```

and there it stays.

Here's my /etc/apt/sources.list:

```

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

Any ideas, guys? I'm totally blocked here. :confused:

---

### Post by taurus on 2007-03-09
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from all the repos.  Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by bspeakmon on 2007-03-09
Done. No change.

---

### Post by taurus on 2007-03-09
And your network is working!

```
ping -c 3 www.google.com
```

---

### Post by bspeakmon on 2007-03-09
Sure is. I'm posting from the machine right now. Ping works too.

---

### Post by taurus on 2007-03-09
Any chance you have proxy running on your machine?  What if you replace the **http **with **ftp** in /etc/apt/sources.list.  See if that works.

---

### Post by bspeakmon on 2007-03-09
Using ftp works fine. (?) Why would that be?

I'm able to hit the server just fine through the browser. And this is a stock install. And I don't have a proxy in my home network anywhere. And 6.10 didn't have this problem.

Very confused. Is there something else that might cause it to work over ftp but not http?

Thanks for the help in any case, I seem to be running now. :)

---

### Post by bspeakmon on 2007-03-09
Quick epilogue:

After downloading the mass of updates and restarting, I tried using http in sources.list again and it worked fine. 

No idea what the problem was, but I doubt it was on my end at this point.

---

