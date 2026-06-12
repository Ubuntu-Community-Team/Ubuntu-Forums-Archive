---
title: "Synaptic Package Manager Error"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by blockdude14 on 2007-03-17
After I start Synaptic I get an error message displaying: 

[B]E: Malformed line 50 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.[/B]

I am a newbie. Please help! I think it's something with the repositories. :confused:

---

### Post by r4ik on 2007-03-17
Could you post you're sources.list 

please?

---

### Post by bapoumba on 2007-03-17
To post your sources.list, please open a terminal (> Accessories > Terminal) and run **cat /etc/apt/sources.list**. Paste the complete output.

---

### Post by blockdude14 on 2007-03-17
Sorry :/ I don't know where it is located. Can u tell me? I'm a newbie.

---

### Post by blockdude14 on 2007-03-17
## Ubuntu 'Main' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted main universe #Added by software-properties

## Ubuntu 'Universe' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

## Ubuntu 'Backports' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe #Added by software-properties

## Ubuntu Bug Fix Updates

## Ubuntu Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

## Canonical 'Commercial' Repository
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Skype - VoIP Client
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by bapoumba on 2007-03-17
> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
You need to delete this line.

Open the terminal again, and run
```
sudo nano -B /etc/apt/sources.list
```
Go down to the quoted line (line #50), remove it.
Save the file with CTRL-O, same name (hit <enter>)
Exit nano with CTRL-X

Reload our source.list file:
```
sudo aptitude update
```
Do you still have errors ? If so, paste them in here.

---

### Post by blockdude14 on 2007-03-17
works great thanks :)

---

### Post by blockdude14 on 2007-03-17
When I clciked reload on package manager i got an error displaying: 
[B]
[http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz:](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz:) 404 Not Found [IP: 38.115.131.24 80][/B]

---

