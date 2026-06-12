---
title: "How to set default repositories"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by FleetAdmiral74 on 2006-09-26
Is there a way I can set the repositories back to the default ones with a clean install? I say this because I get this error message when trying to reload...

E: Type 'test' is not known on line 33 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

I know my little bro decidede to remove one of those Official Ubuntu repositores or two, so I just want to set everything to default. Any help appreciated.

---

### Post by bswilson on 2006-09-26
> **FleetAdmiral74 said:**
> Is there a way I can set the repositories back to the default ones with a clean install? 

As requested.

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
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

---

### Post by FleetAdmiral74 on 2006-09-26
I am pretty new to Ubuntu in general. What do I do with those lines starting with a ##? I think I remember how to use the other ones you listed though.

Sorry I'm asking for clarrification, cause I am sure your answer is complete, but I forgot to mention I'm new >.<

EDIT: Even after removing all the repositories, I still get 

E: Type 'test' is not known on line 23 in source list /etc/apt/sources.list
E: Unable to lock the list directory

Obviously something is there that should not be...thats what I meant be setting everything back to default

---

### Post by FleetAdmiral74 on 2006-09-26
The file indicated in the error message looks like this:



## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


test [http://test](http://test)

That test line at the bottom is wat I think is messing it up, but I cannot edit the doc and save it...I am so confused...

---

### Post by aysiu on 2006-09-26
Press Alt-F2 and type ```
gksudo nautilus
``` Then you can modify the file.

---

### Post by FleetAdmiral74 on 2006-09-26
Thanks! I deleted that one line and everything seems to be back to normal.

---

### Post by randell6564 on 2006-09-26
> **FleetAdmiral74 said:**
> I am pretty new to Ubuntu in general. What do I do with those lines starting with a ##? 
Hi!
You do not do anything with them! What you see there is just a message to the user.  It's the Repositories that you need be concerned with. (The lines WITHOUT the ## next to them.)

'bswilson' was just providing HIS /etc/apt/sources.list for you to copy and paste.

Backup your current sources.list and then make a new one using bswilsons' list!  Then do a [B]sudo aptitude update
[/B]

---

