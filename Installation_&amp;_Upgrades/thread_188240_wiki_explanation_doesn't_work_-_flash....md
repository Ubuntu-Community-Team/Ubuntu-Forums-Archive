---
title: "wiki explanation doesn't work - flash..."
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by fargoth on 2006-06-03
ok, i want to see flash on firefox.
the only flash i find in the repositories is libflash0c2 and libflash-mozdev and they don't seem to do anything... 
(i've enable the universe and multiverse repositories)

the wiki says:
[Quote=wiki]
Ubuntu 6.06 (Dapper Drake)

    *

        sudo apt-get install flashplugin-nonfree
        sudo update-flashplugin
[/Quote]
        

no such file exists... 
where did it go? guess the wiki is out of date...

---

### Post by meng on 2006-06-03
I can see it in my synaptic.
Perhaps you could post your /etc/apt/sources.list ??

---

### Post by fargoth on 2006-06-03
ok... c&p'ed it...
[Quote=sources.list]

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
[/Quote]
oh, and wow, that was a fast response =)

---

### Post by llamakc on 2006-06-03
It's in the multiverse. You'll need to add that.

---

### Post by fargoth on 2006-06-03
uhm, doesn't the line
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
include multiverse?

whats the address of the propper multiverse?

---

### Post by llamakc on 2006-06-03
Sorry, when I scanned your sources.list I didn't see that.

---

### Post by llamakc on 2006-06-03
I have it on the dapper-backports line and also on the 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse

line, just sub your country code, rerun apt-get update and you should be good to go.

---

### Post by fargoth on 2006-06-03
thanks =)
it works now...

---

