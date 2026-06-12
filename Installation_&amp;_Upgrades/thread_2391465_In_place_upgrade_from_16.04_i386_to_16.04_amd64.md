---
title: "In place upgrade from 16.04 i386 to 16.04 amd64?"
date: 2018-05-09
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2018-05-09
Is there any practical to completely upgrade a system from i386 to amd64 without reinstalling? Has anyone successful done it?

I know the usual advise if to do a fresh install, but most of the information available on the web is old and multi-arch has come a long way.

I have one old production machine I think it started out running 6.04 and doing a fresh install with all of the configuration necessary would take it our of service for too long. 

I have tried a couple of times on non-production machines and it's pretty easy to get an amd64 kernel installed and booting with all of the i386 packages running under that. All you really have to do is install a few basic amd64 packages which are mostly identified when you install the amd64 kernel. Replacing all of the other packages seems to run into a lot of missing packages and dependency problems. I end up with a lot of manually installed packages and I can't upgrade reasonably. I'm not sure exactly why apt and dpkg make such a mess of the dependencies between the two architectures..

---

### Post by yancek on 2018-05-09
The link below gives an explanation of how to do it on Debian based systems such as Ubuntu.  Note the warnings at the top of the page, particularly the part which states "This really is for professional-level sysadmins".

[http://users.digitalkingdom.org/~rlpowell/hobbies/debian_arch_up/index.html](http://users.digitalkingdom.org/~rlpowell/hobbies/debian_arch_up/index.html)

---

### Post by Xian on 2018-05-10
I've read of people having done it ... but it's usually after spending a few days resolving package conflicts. 

Yet to see a guide (other than theoretical) on how to do the procedure cleanly.

Another reference if you really want to give it a whack:

[https://wiki.debian.org/CrossGrading#Cross-grading_a_Debian_System](https://wiki.debian.org/CrossGrading#Cross-grading_a_Debian_System)
[https://askubuntu.com/questions/5018/is-it-possible-to-upgrade-from-a-32bit-to-a-64bit-installation](https://askubuntu.com/questions/5018/is-it-possible-to-upgrade-from-a-32bit-to-a-64bit-installation)

&#129310;

---

### Post by TheFu on 2018-05-10
No.  You'll end up with a partially borked system unless you are an expert.

OTOH, you can backup data and lists of packages to make  the migration a little easier.  **Aptik** should help.

Really, with Linux systems, having versioned backups is fairly trivial these days.  Just backup the data and settings, but not program binaries.

---

### Post by rsteinmetz70112 on 2018-05-10
Thanks of the responses. I have looked at the suggested pages and the AskUbuntu pages is old. I'v mot sure how old the digitalkingdom page is but seem old. The most recent seem to be the Debian WIKI which was updated this year. 

I'm really kind of surprised this has not been worked out yet.

---

### Post by yancek on 2018-05-10
> I'm really kind of surprised this has not been worked out yet.

I would not expect that to happen since 64 bit computers for personal computers were first used in 2003.  Ubuntu no longer has 32 bit systems available for download.  If you read the link I posted, you can see it is a convoluted process and I doubt any developers are going to spend time on it.

---

### Post by oldos2er on 2018-05-11
> **rsteinmetz70112 said:**
> I'm really kind of surprised this has not been worked out yet.

As yancek implied, there's really nothing to work out, because what you said in your first post > doing a fresh install with all of the configuration necessary would be a far *less* time-consuming task than trying to do something e.g. that outlined in [http://users.digitalkingdom.org/~rlpowell/hobbies/debian_arch_up/index.html](http://users.digitalkingdom.org/~rlpowell/hobbies/debian_arch_up/index.html)

---

