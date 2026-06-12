---
title: "software doesnt get installed from ubuntu software centre"
date: 2014-01-25
forum: Installation &amp; Upgrades
---

### Post by jrmchess on 2014-01-25
I have ubuntu 12.04.03. But I can't seem to install software from the ubunut software centre. Whenever I click install it shows the progress bar progressing but when I check the "dash home" it doesnt show up. I have to install it manually from the terminal. Is there a fix to this? 


Thanks

---

### Post by MG&amp;TL on 2014-01-25
Does this happen for *all* software, (i.e. software you know to have worked before), or just a specific piece of software? Some software doesn't support the protocols required to have an icon in the Dash.

---

### Post by grahammechanical on 2014-01-25
I think that Dash>Home is the wrong place to look. Dash>Home>Applications is for recently used applications. Try Dash>Applications>Installed - see more results. We can use Super (windows) key + A. We can also filter results into different categories.

Regards.

---

### Post by jrmchess on 2014-01-25
> **MG&TL said:**
> Does this happen for *all* software, (i.e. software you know to have worked before), or just a specific piece of software? Some software doesn't support the protocols required to have an icon in the Dash.

I tried gnucash, alarm clock, wine but none of them got installed. I had to install them from the terminal. I did a search in dash home but couldnt find them after installation from the ubuntu software centre

---

### Post by MG&amp;TL on 2014-01-26
Try running

```
software-center
```

from your terminal, then try installing something in the application you just launched. Post any output you get. :-)

---

### Post by jrmchess on 2014-01-26
> **MG&TL said:**
> Try running

```
software-center
```

from your terminal, then try installing something in the application you just launched. Post any output you get. :-)

sorry but this didnt fix the issue. it's still the same

---

### Post by philinux on 2014-01-26
Were there any error messages in the terminal that you ran the SC from?

---

### Post by jrmchess on 2014-01-26
no I did not check but I dont think there were any as the ubuntu software got installed

---

### Post by philinux on 2014-01-26
> **jrmchess said:**
> no I did not check but I dont think there were any as the ubuntu software got installed

No idea what the above means.  Did software center work or not?

---

### Post by jrmchess on 2014-01-27
> **philinux said:**
> No idea what the above means.  Did software center work or not?

I dont think there were any error msgs but software centre is still not working after trying out the script in the terminal. I tried to install something and it showed as being installed but actually didn't

---

### Post by philinux on 2014-01-27
Are any errors reported in the terminal when you run this.

sudo apt-get update 

Followed by

sudo apt-get upgrade

---

### Post by jrmchess on 2014-01-28
> **philinux said:**
> Are any errors reported in the terminal when you run this.

sudo apt-get update 



E: GPG error: [http://deb.torproject.org](http://deb.torproject.org) precise Release: The following signatures were invalid: NODATA 1 NODATA 2


> 
Followed by

sudo apt-get upgrade

this the error I got...:(

---

### Post by philinux on 2014-01-28
Let's look at your sources list,

```
cat /etc/apt/sources.list
```

copy and paste the output. Don't forget to put code tags around it.

---

### Post by jrmchess on 2014-01-28
> **philinux said:**
> Let's look at your sources list,

```
cat /etc/apt/sources.list
```

copy and paste the output. Don't forget to put code tags around it.

```
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://deb.torproject.org/torproject.org precise main
deb-src http://deb.torproject.org/torproject.org precise main


```

---

