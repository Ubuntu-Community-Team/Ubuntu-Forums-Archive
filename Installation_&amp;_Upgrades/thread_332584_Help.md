---
title: "Help"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by Bigadada_saba on 2007-01-06
Hi  can any one help me with this problem
 whenever i try to update i get this error message

E: Type "wget" is not known on line 39 in source list /etc/apt/sources.list, E: The list of sources could not be read.


need help to update my machine.

---

### Post by taurus on 2007-01-06
There is something wrong with your /etc/apt/sources.list especially line 39.  So, post your /etc/apt/sources.list here if you wish...

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Bigadada_saba on 2007-01-06
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main
deb [http://ai.archive.ubuntu.com/ubuntu/](http://ai.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://ai.archive.ubuntu.com/ubuntu/](http://ai.archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ai.archive.ubuntu.com/ubuntu/](http://ai.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://ai.archive.ubuntu.com/ubuntu/](http://ai.archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ai.archive.ubuntu.com/ubuntu/](http://ai.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ai.archive.ubuntu.com/ubuntu/](http://ai.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ai.archive.ubuntu.com/ubuntu/](http://ai.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ai.archive.ubuntu.com/ubuntu/](http://ai.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe #Added by software-properties

wget [http://www.getautomatrix.com/apt/key.gpg.asc](http://www.getautomatrix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C
sudo apt-key add
sudo apt-get update

exit
wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)

gpg --import key.gpg.asc

gpg --export --armor 521A9C7C | sudo apt-key add -

sudo apt-get update
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

### Post by taurus on 2007-01-06
You tried to add a repo for automatix but you added too many lines in there...  Therefore, you need to remove everything from "wget" until the second to the last line!

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Remove these lines (leave the last line alone)...

```

wget http://www.getautomatrix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C
sudo apt-key add
sudo apt-get update

exit
wget http://www.getautomatix.com/apt/key.gpg.asc

gpg --import key.gpg.asc

gpg --export --armor 521A9C7C | sudo apt-key add -

sudo apt-get update

```
Save the changes and at the prompt, run

```

wget http://www.getautomatrix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
sudo aptitude update
sudo aptitude install automatix2

```

---

### Post by Bigadada_saba on 2007-01-06
when i run this in the terminal this is what i get is it correct



 [http://www.getautomatrix.com/apt/key.gpg.asc](http://www.getautomatrix.com/apt/key.gpg.asc)
--11:02:29--  [http://www.getautomatrix.com/apt/key.gpg.asc](http://www.getautomatrix.com/apt/key.gpg.asc)
           => `key.gpg.asc.2'
Resolving [www.getautomatrix.com](www.getautomatrix.com)... 204.13.161.33
Connecting to www.getautomatrix.com|204.13.161.33|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
11:02:30 ERROR 404: Not Found.

---

### Post by taurus on 2007-01-06
Perhaps the site is currently down!  What's the output of you run this command from a terminal?

```
ping -w 3 www.yahoo.com
```

---

### Post by Bigadada_saba on 2007-01-06
thanks every thing is working good now


i love linux 
cause with windows this would not be possible

---

### Post by taurus on 2007-01-06
So you are able to install automatix2 now!

---

### Post by Bigadada_saba on 2007-01-06
yes thanks

---

