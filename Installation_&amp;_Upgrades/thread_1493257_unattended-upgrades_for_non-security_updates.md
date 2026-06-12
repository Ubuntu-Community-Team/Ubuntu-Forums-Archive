---
title: "unattended-upgrades for non-security updates"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by rayrayyy on 2010-05-25
I've recently installed the unattended-upgrades package on a few Ubuntu 9.04 servers, and it's working great to automatically install security upgrades.  However, is there a way to have non-security upgrades automatically installed as well?  The README for unattended-upgrades says it'll do security ones only. 

My main goal is to have all package upgrades be installed unattended except for kernel and libc upgrades (I want to do those manually on my own time).  I guess I could write a script that does 'apt-show-versions -u' to get a list of upgradable packages and then do 'apt-get install' on the packages if their names don't match  linux-server, linux-image-server, or libc*, but I was hoping there's an easier way to accomplish this.

I've looked at 'aptitude safe-upgrade -y', but I think that'll install kernel and libc upgrades.

---

### Post by cariboo on 2010-05-25
On 9.04 all the updates are security updates, there are no new packages available.

---

### Post by rayrayyy on 2010-05-26
Right now I'm seeing that the byobu package is upgradeable, and it's a non-security update:

$ apt-show-versions -u
byobu/jaunty upgradeable from 2.75-0ubuntu1~ppa3 to 2.76-0ubuntu1~ppa2
libc6/jaunty-security upgradeable from 2.9-4ubuntu6.1 to 2.9-4ubuntu6.2
libc6-dev/jaunty-security upgradeable from 2.9-4ubuntu6.1 to 2.9-4ubuntu6.2


My unattended-upgrades cron job is correctly skipping these because byobu is non-security, and I've blacklisted libc upgrades.  So what I was looking for was some unattended way to upgrade byobu and any other non-security updates.

I'll just write a script to do this for now until I find some easier way.

---

### Post by nanonils on 2011-01-29
Working now: [http://ubuntuforums.org/showthread.php?t=1401845](http://ubuntuforums.org/showthread.php?t=1401845)
This took me for ever to figure out as a noob so I figured I could as well point other old/cold threads to the above one.
Thanks!

---

