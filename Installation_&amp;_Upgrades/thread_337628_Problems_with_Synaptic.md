---
title: "Problems with Synaptic"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by geek-o-logist on 2007-01-13
Hi ... I tried to install Automatix and ended up screwing my installation.   I see the following error:

E:Type '"deb' is not known on line 34 in source list/etc/apt/sources.list
E:The list of sources could not be read

Pls help to avoid a re-installation

---

### Post by taurus on 2007-01-13
Something is wrong with line 34 in your /etc/apt/sources.list.  If you are not sure how to fix it, then post your /etc/apt/sources.list here then.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by geek-o-logist on 2007-01-13
Hi .... Thanks 

I tried using the terminal but got an error, however, I have copied the /etc/apt/sources.list and the same is as follows:


deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
"deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main"
"deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main"]

---

### Post by taurus on 2007-01-13
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Then, remove the last line and remove the " " from the one above it.

Remove this one:
```

"deb http://www.getautomatix.com/apt dapper main"]

```

Remove the " " from this line:
```

"deb http://www.getautomatix.com/apt dapper main"

```

---

### Post by Sense on 2007-01-13
> **geek-o-logist said:**
> Hi .... Thanks 
...
"deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main"
"deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main"]
That is the error. Remove the " and the ] and everything should work.

EDIT:Oops, when I pushed the Post reply button, there wasn't a reply. But now there is one, just before me and more detailed.

---

### Post by geek-o-logist on 2007-01-13
Thanks a lot .... that worked!! You have helped me avoid a reinstall .... Thanks !!

---

