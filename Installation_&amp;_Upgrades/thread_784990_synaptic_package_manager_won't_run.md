---
title: "synaptic package manager won't run"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by jasonsexton on 2008-05-07
[FONT="Arial Black"]after doing the Hardy upgrade from 7.10 I can not run synaptic package manager.  I get the following message:[/FONT]

E: Malformed line 37 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

[FONT="Arial Black"]this is what the sources list looks like from konsole:[/FONT]

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://ubuntu.org.au/getdeb/](http://ubuntu.org.au/getdeb/)
deb [http://ubuntu.org.au/getdeb/](http://ubuntu.org.au/getdeb/)
deb [http://ubuntu.org.au/getdeb/](http://ubuntu.org.au/getdeb/)

any help greatly appreciated...thanks in advance

---

### Post by tamoneya on 2008-05-07
comment out the last three lines.  Then test it.

---

### Post by jasonsexton on 2008-05-07
sorry for my lack of knowledge, but I am unfamiliar with comment out?  and how I test it.

---

### Post by lsmobrian on 2008-05-07
# designates a comment. just put a # before each of the last 3 lines and try running your update/upgrade again

---

### Post by tamoneya on 2008-05-07
you will notice that most of the lines in the file you posted start with a "#".  This tells the computer to not read those lines and they are "commented out".  Then you should just run the package manager again and see if it works.  It may also require a restart but I think it should be alright without it.

---

### Post by jasonsexton on 2008-05-07
that worked great, problem seems to be solved.  thank you for the help, I learned a lot.  do I need to close the thread or anything?

---

### Post by tamoneya on 2008-05-07
you dont want to close a thread and actually you cant since it can only be done my a mod or admin.  It should be kept open so that users with similar problems could reply in the future.  Typically I would say mark thread as solved as you can see in my sig.  This is done by going into thread tools which is directly above your first post.  However since the forum upgrade a couple of weeks ago this still hasnt been reimplemented :(  The other thing some people do is thank posters for especially helpful post by clicking the little blue ribbon with a star button in the lower right of each post. You could however do nothing and the thread would be properly finished.

---

### Post by jasonsexton on 2008-05-07
thanks again.  this forum rocks!:guitar:

---

### Post by jasonsexton on 2008-05-07
testing my signature

---

### Post by tamoneya on 2008-05-07
seems to be working pretty well.  Welcome to the forums.  Good luck with Ubuntu.

---

### Post by jasonsexton on 2008-09-26
problem solved

---

### Post by jasonsexton on 2009-01-23
solved

---

