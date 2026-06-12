---
title: "[SOLVED] synaptic manager problem"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by arturieto on 2008-06-08
recently i opened my laptop and wish to update all my repositories.  I got this message:

E:*Malformed line 75 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'*

Please help what shall i do.

---

### Post by Pumalite on 2008-06-08
Post your sources.list. You might need a new one.

---

### Post by Nikitas350 on 2008-06-08
Open terminal and run "gksudo gedit /etc/apt/sources.list". Then replace everything with this:

-----START---- (do not include this line)
#
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---END----(do not include this line)

Then run sudo apt-get update
Good luck ;)

---

### Post by Nikitas350 on 2008-06-08
(this post was posted by mistake)

---

### Post by meindian523 on 2008-06-08
Just check line 75 in your sources.list for any errors.Correct those and you are good to go.Open sources.list using ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by arturieto on 2008-06-08
my everdearest partner

thank you very  much for the advise.  I did edit the last line 75. just erase it and save the list. then run synaptic gui. it runs. again thank you very much.

am arturieto ramigoso from the Philippines. am new to ubuntu.  i like it very much. please reply through e-mail.  my e-mail is [email]arturieto_ramigoso@yahoo.com[/email].

again thank you

---

### Post by meindian523 on 2008-06-09
Don't post your email on public forums such as these,spam bots are always on the lookout for them.

---

### Post by arturieto on 2008-06-10
thanks again for the advise.

---

### Post by meindian523 on 2008-06-11
Also,please mark your thread solved.

---

