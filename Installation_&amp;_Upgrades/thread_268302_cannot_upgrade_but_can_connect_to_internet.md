---
title: "cannot upgrade but can connect to internet"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by londonbabs on 2006-09-29
...I need quite some help, I checked everything that was possible, changed my sources.list so many times I can't count, I'm pretty sure my resolve.conf is well configurated and I blacklisted ipv6 business,but still can't update and keep getting the same error messages listed in so many peoples cases which I already read about (namely:

Errhttp://archive.ubuntu.com dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Errhttp://wine.budgetdedicated.com dapper Release.gpg
  Could not connect to wine.budgetdedicated.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Errhttp://packages.freecontrib.org dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (1.0.0.0). - connect (101 Network is unreachable)
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Errhttp://gb.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Errhttp://gb.archive.ubuntu.com dapper Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)...so long so forth)
 
Now, I'm definitely not familiar yet with ubuntu or linux in general, quite newby actually, so if anyone thinks they could help, I'll be more than grateful, I feel totaly stuck n cannot use anything, I do connect to the net, but cannot install any package or anything, let alone updates
my sources.list :

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the ‘universe’
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the ‘backports’
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

## WINE
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

#PLF Repositories
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free

(P.S. I live in UK)

my resolv.conf :
nameserver 192.168.1.1
nameserver 192.168.1.2

(I also tried with my provider IP, looks like this
 nameserver 192.168.1.1
 nameserver 194.168.54.50 or this one alone,
 but to no avail)

I'm in such need of help I'm even considering switching back to windows (well, I also have linspire, which was working pretty fine, but I wouldn't learn anything about linux with this one... I just find ubuntu perfect for someone as new as I am but that still wants to learn some stuffs about the linux platform) 
...but going backward now would truly be the end of my computer, seeing as I used to kick it in the teeth so much while using frustrating window...
anybody ?? I really like ubuntu distro and would like to carry on using it
(btw I use a D-Link g604t wireless router if it's got anything to do with anything...)

---

### Post by aysiu on 2006-09-29
It sounds as if you've already done quite a bit of research, but just in case someone can offer insight into your problem, can you post the exact output of this command? ```
sudo aptitude update
```

---

### Post by morphodone on 2006-09-29
I wonder if that server is down, you could try using the United States mirrors.

edit: nevermind

---

### Post by londonbabs on 2006-09-29
here goes...

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
  Could not connect to wine.budgetdedicated.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
13% [Connecting to gb.archive.ubuntu.com (1.0.0.0)] [Connecting to archive.ubuntu...

and it goes on and on to tell me that it didn't work... do you want the whole results ?

---

### Post by aysiu on 2006-09-29
Never having experienced this myself, I have no idea what might work or not, but [this thread](http://ubuntuforums.org/showthread.php?t=206692) seems to have a number of different solutions (read all three pages). I think they're worth a try.

---

### Post by londonbabs on 2006-09-29
I tried replacing all the <gb.> with <us.> or even <uk.> but to get the same results... cannot be all the servers now... it's been going on for the last 2 days at least...

---

### Post by londonbabs on 2006-09-29
thanks for the link, but I spend the last half hour reading it (I even left a message on it, but thought better and opened a new thread)
still didn't help, I tried all combinations I could see... but still nothing
thanks for the fast answer though
anybody thinking of anything I'm doing wrong ?

---

### Post by aysiu on 2006-09-29
Wow! I thought that thread had everything. Guess not. So it wasn't even the router blocking the word *dapper* (I thought that was kind of funny)?

---

### Post by morphodone on 2006-09-29
can you bring any of those links up in a web browser?

[http://archive.ubuntu.com/](http://archive.ubuntu.com/)

---

### Post by londonbabs on 2006-09-29
yes I can see the directory in a browser and also go through it, but it looks very much as a maze to me, as for my router blocking a word, I wouldn't know how to check this out, let alone sort it...

---

### Post by londonbabs on 2006-09-30
still nothing going on...
maybe I could try to find out if my router is blocking anything... but as far as I'm comcerned, I don't think I have the necessary knowledge to do so
I'll try, but if anybody got any ideas when it comes to this matter with the D-Link G604T, any pointers would be greatly appreciated
thanks already

---

### Post by Ferk on 2006-10-01
I have exactly the same problem...

I managed to overcome it making a simple script that pings all the adresses in sources.list

It seems that after a ping to the direction, the IP of that site resolves without issues and you dont get that f***ng 1.0.0.0 IP

however I still cant conect bittorrent, azureus nor amule.. nor some other apps..
And the need of the ping script makes installing uncomfortable

I hope we can find a better way

---

### Post by londonbabs on 2006-10-01
whoa, you think that'd be the only way ?? If you find a minute to explain how to do just that, I'll try it out
And pray to try and find a solution on my own with my limited knowledge in this O.S.
thanks for the replies in the meantime
if anybody else is thinking of anything that could help, don't be shy, am still convinced there must be a workaround or something to fix this

---

### Post by londonbabs on 2006-10-01
here's my latest sources file:

    ## Add comments (##) in front of any line to remove it from being checked.
    ## Use the following sources.list at your own risk.

    deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
    deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

    ## MAJOR BUG FIX UPDATES produced after the final release
    deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
    deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

    ## UBUNTU SECURITY UPDATES
    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

    ## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
    deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
    deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

    ## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
    deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
    deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

and for god knows what reasons, this seems to work... I'm pretty sure I used that before to no avail, it just magical here...
well, I'll have to see what happens when I restart, but it seems ok  now, thanks for all who helped again !!

---

### Post by londonbabs on 2006-10-01
oooookaaay... I updated... once ! now everything's stuck again... how's that possible, I don't get it...
my sources are still the same after reboot, I can even access them on the net through a browser...
anyone familiar with this, updates working once then blocking ??
I am close to madness with all those stories, any help ? anyone ?

---

