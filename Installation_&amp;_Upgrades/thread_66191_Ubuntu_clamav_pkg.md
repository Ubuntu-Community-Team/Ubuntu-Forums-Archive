---
title: "Ubuntu clamav pkg"
date: 2005-09-16
forum: Installation &amp; Upgrades
---

### Post by CYHPT.net on 2005-09-16
Hi all,

Can someone here please tell me how I could get the clamav for ubuntu pkg instead of having to dl from clamav site and compile it?

I wanna do apt-get install clamav, but it doesnt seem to have it when I install ubuntu. Thanks guys.

---

### Post by KingBahamut on 2005-09-16
[QUOTE=CYHPT.net]Hi all,

Can someone here please tell me how I could get the clamav for ubuntu pkg instead of having to dl from clamav site and compile it?

I wanna do apt-get install clamav, but it doesnt seem to have it when I install ubuntu. Thanks guys.[/QUOTE]
 Got all the repositories from the ubuntuguide.org site? 

if so , shouldnt be a problem in finding it.

---

### Post by CYHPT.net on 2005-09-17
[QUOTE=KingBahamut]Got all the repositories from the ubuntuguide.org site? 

if so , shouldnt be a problem in finding it.[/QUOTE]
 Ah ok, thanks.

---

### Post by XDevHald on 2005-09-17
I could be wrong, but don't the backports have this packaged?

---

### Post by jdong on 2005-09-17
[QUOTE=Steve Myers]I could be wrong, but don't the backports have this packaged?[/QUOTE]

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=clamav](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=clamav)

Certainly :)

---

### Post by XDevHald on 2005-09-17
[QUOTE=Steve Myers]I could be wrong, but don't the backports have this packaged?[/QUOTE]
 I am going to put a request to the backports team so they can put the latest stable release of clamav.

The most recent one is 0.86.2-5 (newest version is 0.87) in which the new version will be sent as a requested backport.

**EDIT:** Thanks jdong!
**EDIT #2: **The request has been placed and can be viewed here: [http://ubuntuforums.org/showthread.php?p=356363#post356363](http://ubuntuforums.org/showthread.php?p=356363#post356363)

---

### Post by majikstreet on 2005-09-17
[QUOTE=Steve Myers]I am going to put a request to the backports team so they can put the latest stable release of clamav.

The most recent one is 0.86.2-5 (newest version is 0.87) in which the new version will be sent as a requested backport.

**EDIT:** Thanks jdong!
**EDIT #2: **The request has been placed and can be viewed here: [http://ubuntuforums.org/showthread.php?p=356363#post356363](http://ubuntuforums.org/showthread.php?p=356363#post356363)[/QUOTE]
 For curiosities sake, why do you need an anti-virius on linux?

---

### Post by jdong on 2005-09-17
I'm not gonna backport 0.87 for Hoary until we have it in Breezy-security (since it's a security fix) or breezy+1....


As far as purpose, mostly mail or file server scanner for Windows boxes.

---

### Post by XDevHald on 2005-09-17
[QUOTE=jdong]I'm not gonna backport 0.87 for Hoary until we have it in Breezy-security (since it's a security fix) or breezy+1....


As far as purpose, mostly mail or file server scanner for Windows boxes.[/QUOTE]
 Sounds good to me Jdong :) I am running Colony 4 right now, and can't wait for the new release, should be top notch and Dapper will kcik ass as well :D

ClamAV is great for for exactly what Jdong said.

---

### Post by CYHPT.net on 2005-09-18
Im kinda lost here since Im new to ubuntu linux. What do u mean by backports? And also how do I check the version of clamav Im running on ubuntu?

Thanks

---

### Post by XDevHald on 2005-09-18
You can view it by Synaptic by opening this application in the System> Administration > Synaptic and then click the SEARCH tool button and type clamav, this you can see the version given in the screen shot below.

[[img]http://img86.imageshack.us/img86/4237/screenshot3ft.th.png[/img]]("http://img86.imageshack.us/my.php?image=screenshot3ft.png")
[[img]http://img86.imageshack.us/img86/4237/screenshot3ft.th.png%5D[/img]]("http://img86.imageshack.us/my.php?image=screenshot3ft.png")

---

### Post by jdong on 2005-09-18
[QUOTE=CYHPT.net]Im kinda lost here since Im new to ubuntu linux. What do u mean by backports? And also how do I check the version of clamav Im running on ubuntu?

Thanks[/QUOTE]

Ubuntu releases a stable version every 6 months. The latest stable release is "5.04. Hoary Hedgehog", released in April 2005 (200**5/04**). Once a stable release is made, in order to keep it stable, Ubuntu does not update any software included. For example, if Hoary shipped with Firefox 1.0, it will not receive an upgrade to Firefox 1.5 if it's released during Hoary's lifetime. Security updates are furnished for a core subset of packages by isolating the source code changes specifically for the security issue, and bringing those changes back to the shipped version of the software.


However, back in October 2004, I believed that Ubuntu **can** find balance between new software and stability, and launched the Ubuntu Backports project to explore that balance. I simply take packages from development versions of Ubuntu (which are naturally newer/newest) and compile them against Hoary, making them 100% compatible with the existing environment, without causing adverse side effects to existing software.

Since then, Ubuntu Backports project has been integrated with Ubuntu to become the "Ubuntu Backports Team"...

Basically, all you need to know is that Backports offers newer software.

---

### Post by CYHPT.net on 2005-09-20
Ah ok... cool.... Thanks for that info jdong.

Also, when I tried to compile clamav that I downloaded off from clamav site, it doesnt seem to work.. is there a reason why? Thanks

---

### Post by CYHPT.net on 2005-09-20
Also, whats a synaptic? >.<

---

### Post by XDevHald on 2005-09-20
[QUOTE=CYHPT.net]Also, whats a synaptic? >.<[/QUOTE]
 Synaptic is a package manager in which holds all applications of Ubuntu & KDE for basically everything you need out of an OS of Linux.

Please take a look at Synaptics home page and see exactly what they're all about :) [http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/)

---

### Post by CYHPT.net on 2005-09-21
[QUOTE=Steve Myers]Synaptic is a package manager in which holds all applications of Ubuntu & KDE for basically everything you need out of an OS of Linux.

Please take a look at Synaptics home page and see exactly what they're all about :) [http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/)[/QUOTE]
 Ah ok... thanks for the advice and the link... :)

---

