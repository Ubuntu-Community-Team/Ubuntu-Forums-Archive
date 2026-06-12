---
title: "Is Gutsy really out?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by geeree on 2007-10-18
Has anyone tried to upgrade to Ubuntu 7.10 from 7.04, following this "officially recommended" procedure?

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) 

I have been trying to do that for four hours now. But the expected message "New distribution release '7.10' is available" simply won't come up! I described my problem here 

[http://ubuntuforums.org/showthread.php?t=579511](http://ubuntuforums.org/showthread.php?t=579511)

but mine seems to be a rare case. I don't understand what is going wrong. 

Girish.

---

### Post by glendavee on 2007-10-18
I've just upgraded from 7.04 following the procedure and so far, seems to have worked. You need to check for updates before the new distribution message comes up, I think

---

### Post by geeree on 2007-10-18
> **glendavee said:**
> I've just upgraded from 7.04 following the procedure and so far, seems to have worked. You need to check for updates before the new distribution message comes up, I think

Well, I did that! Would you mind showing your /etc/apt/sources.list please! 

Thanks.
Girish.

---

### Post by glendavee on 2007-10-19
Here it is 

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

Hope this helps

---

### Post by geeree on 2007-10-20
Thanks, glendavee, it did help. I had to remove the medibuntu lines it seems. (Though I don't understand why!) It all got sorted out a while ago and I am on Gutsy right now! 

Girish.

---

