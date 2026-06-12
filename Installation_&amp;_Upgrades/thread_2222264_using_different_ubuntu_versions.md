---
title: "using different ubuntu versions"
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by Deb_T. on 2014-05-05
Hi all,

I am relatively new to ubuntu and maintain three machines (two for processing, one for backup) running 12.04. I'd like to upgrade to 13.10 and have two concerns. The first involves incremental backups. I've read that it's not recommended to jump between releases and that I should instead upgrade incrementally until I reach 13.10. Has anyone found this not to be the case (i.e., I could upgrade to 13.10 without problems)? My second concern is that one of the processing machines has a long job running on it and the user can't give an estimate as to when it might complete. I am wondering about having one machine with 12.04 while the other two are running 13.10. We share files and software between the two processing machines and both will be backing up to the machine upgrading to 13.10. If anyone foresees problems, I can just wait to upgrade all three simultaneously. 

Thanks!
Deb

---

### Post by deadflowr on 2014-05-05
Instead of updating from 12.04 to 13.10. wait for 14.04 to hit its first point release, and then upgrade directly to that.
Upgrading from 12.04 to 13.10, if not doing so with a fresh installation, means you have to upgrade first to 12.10, then to 13.10( Luckily you will skip 13.04). Each upgrade is always fraught with danger( whether remote or not). so additional upgrades means the chances of said danger are all the more possible.

LTS releases, such as 12.04 and 14.04 issue what are called point releases. These are points when the initial bugs and problems found within the version have been generally quashed.( Though not all bug, unfortunately, have been quashed).
The first point release is generally when the ability for those running 12.04(or any LTS) are given the means to upgrade to the next LTS. 
Points release have several point throughout an LTS release, the first being simply one where a lot of code and bugs are cleaned up.It's ideal for those running productivty machines.
The next point releases after, usually contain upgraded Hard Stacks, so those on newer machines can run the older release. As well they also get continued bug-fixes and other updates.


Beyond just that, 13.10 will run of support around the same time the first point release comes, so you will have to upgrade to that anyway.
[URL="https://wiki.ubuntu.com/LTS"]
More on LTS[/URL]
[More on releases]("https://wiki.ubuntu.com/Releases")
[A little more on point releases]("http://askubuntu.com/questions/106159/what-are-point-releases-in-lts-versions")

To note, point releases are "Rolling" so if you install 14.04.1, and keep it updated, you will get 14.04.2 and beyond. You just won't upgrade the hardware stack which is fine.

Hope this helps you, somewhat.

---

### Post by kc1di on 2014-05-05
Hi Deb_T., Welcome to Ubuntu Forums.  It's hard to say what  problems you might run into.  some people upgrade version with no problems.  Others find it breaks things. 
it mostly due to hardware.  But if it were me I would not upgrade to 13.10 because it's support only last for about 8 more months I'd go for 14.04 which is a long term supported version like 12.04.  
I personally prefer fresh installs to upgrade, but as I said some have good success doing upgrades.  **[COLOR="#FF0000"]Back up everything first![/COLOR]**

---

### Post by Deb_T. on 2014-05-08
Thanks to you both!  Looks like updating to 14.04 is the way to go.  I appreciate your advice and suggestions. 

DebT.

---

