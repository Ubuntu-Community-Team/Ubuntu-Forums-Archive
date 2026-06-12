---
title: "Update issues"
date: 2020-02-02
forum: Installation &amp; Upgrades
---

### Post by sool82 on 2020-02-02
Hello,
 

 I've been having issues trying to update anything; I initially was trying to update Firefox unsuccessfully, then tried to install both Chrome and another Ubuntu-offered browser (Midori). Essentially when I attempted to update through the terminal, it would begin the update, then all of the files failed to download.. It seems to indicate my internet connection is the problem, but I'm hard wired and am on the forum here so don't believe that's the case.  
 

 I actually tried then to do a general update 'sudo apt-get update', and was hit with the same failure to download. I can copy/paste the results, sorry I know a screenshot would be better.
 ____________________________________________________________________________
 W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources)  404  Not Found [IP: 2001:67c:1560:8001::29 80] 
  
 W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1560:8001::29 80] 
  
 W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1560:8001::11 80] 
  
 W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1560:8001::11 80] 
  
 E: Some index files failed to download. They have been ignored, or old ones used instead. 
 ____________________________________________________________________________
 

 This is the bottom half of the results also, for the sake of a super long post I didn't include the entire thing.
 

 Does anyone have a workaround or solution to this? I appreciate it :)

---

### Post by CelticWarrior on 2020-02-02
You're using an old release 11.04 that's unsupported since January 2012, so you're missing 8 years of security updates. Using it connected to the internet is now extremely dangerous. Also that's the reason why you can't update or install new software from the repositories.

Pretty please, install a supported release.

---

### Post by ajgreeny on 2020-02-02
The version of Ubuntu you have, 11.04, has been out of support now for several years and the repositories of packages needed to download new applications, or update existing ones no longer exist where they were.  It is therefore impossible for you to update or safely use your version as it has had no security updates for 8 years.

I highly recommend that you clean install a supported version  and install either 18.04, supported until 2023, or 19.10, though with the latter you will need to upgrade to or clean install 20.04 when 19.10 loses support in July 2020.

An online upgrade is impossible from 11.04, so forget about that as a possibility and clean install as above.

Ninja'd by CelticWarrior!

---

### Post by sool82 on 2020-02-02
Thanks Celtic, is it possible to update to 11.10 through the update manager while I'm still running 11.04? I've gotten similar errors before it could complete the download.. Would I need to go the USB stick route on another computer, then plugging and installing it onto this (11.04) system?

---

### Post by sool82 on 2020-02-02
Got it on the clean install 8-) Thanks for your help both of you!

---

### Post by CelticWarrior on 2020-02-02
Quoting from the previous post:

> An online upgrade is impossible from 11.04, so forget about that as a possibility and clean install as above.

That means from scratch, with installation media, preferably USB, of course.

---

