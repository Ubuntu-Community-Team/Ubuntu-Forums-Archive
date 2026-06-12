---
title: "Installing DAR in Intrepid 8.10"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by espressoguy on 2011-07-05
I'm trying to install DAR ("Disk Archive utility") in Intrepid 8.10.  I get these errors:

Err http://us.archive.ubuntu.com intrepid/universe libdar64-4 2.3.8-1
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com intrepid/universe dar 2.3.8-1
  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dar/libdar64-4_2.3.8-1_i386.deb  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dar/dar_2.3.8-1_i386.deb  404 Not Found [IP: 91.189.88.40 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


How do I get DAR in intrepid?

---

### Post by An Sanct on 2011-07-05
> **espressoguy said:**
> Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dar/libdar64-4_2.3.8-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dar/libdar64-4_2.3.8-1_i386.deb)  404 Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dar/dar_2.3.8-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dar/dar_2.3.8-1_i386.deb)  404 Not Found [IP: 91.189.88.40 80]

That version is not present any more, if you browse through this directory: [http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dar](http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dar), you will see it has been removed and replaced by a never version (2.3.9 / 2.3.10)

From the list find the version, that suites your architecture and install it from there (the deb package)

Also, try the '--fix' thing apt is suggesting :) it normally helps ;)

---

### Post by mörgæs on 2011-07-05
Or even better: Begin with a clean install of a supported version of Ubuntu.

---

### Post by espressoguy on 2011-07-05
> **An Sanct said:**
> 
... install it from there (the deb package)

Also, try the '--fix' thing apt is suggesting :) it normally helps ;)

I thought of installing the deb package but when looking at the dependencies I noticed that the required versions  for several of the dependencies didn't even show as "latest available" in synaptic.  So I thought that if I started installing the deb for DAR, I might end up installing 20 or 30 dependency debs before I was done and that there must be a cleaner way.  

Also, regarding --fix, it would seem to me that that approach might not be best for this situation since it might just send me down a dependency rabbit-hole (ie: would have to go find lots of missing dependencies)

---

### Post by espressoguy on 2011-07-05
> **mörgæs said:**
> Or even better: Begin with a clean install of a supported version of Ubuntu.

Yes, I realize I may have to go that route but right now it would be awkward.  I'm wondering: does it sometimes happen that an "upgrade" (ex: 8.10 to 11.04) isn't quite as good as a fresh install on a wiped-clean partition?

---

### Post by mörgæs on 2011-07-05
Yes, it happens more than often. 

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by An Sanct on 2011-07-05
Yes :) its always best, if you to install a clean version, if it can be done.

That is why people use different locations for the home location, so that desktop and other user specific data is not wiped after a fresh install.

---

### Post by Bucky Ball on 2011-07-05
> **espressoguy said:**
>  ... an "upgrade" (ex: 8.10 to 11.04) ...

... would be impossible. You would need to go through upgrading to the next release, then the next, and because 8.10 and a release or two above that are no longer supported you would have some good deal of trouble trying. You can't upgrade straight from 8.10 ->11.04 (nor can you do that from many other releases, always from LTS release to the next LTS release, though).

---

### Post by espressoguy on 2011-07-05
Okay so in a situation like mine where I'm considering migrating from 8.10 to (for example) 11.04 what is the best way (if any) to get a list of all packages that I have installed on top of the original packages that come with the 8.10 installer by default?

Is there any easy way to do a MySql migration in a situation like this?

---

### Post by mörgæs on 2011-07-05
> **espressoguy said:**
> what is the best way (if any) to get a list of all packages that I have installed on top of the original packages that come with the 8.10 installer by default?


It is explained in the link I posted above. I am not sure I would recommend it, though, when upgrading from such an old release.

---

### Post by espressoguy on 2011-07-06
Thanks for the help everyone!  I think the only realistic solution at this point is to upgrade to 11.04 on a fresh partition.  Regarding the installed apps, I'm thinking that if I save the output of the "dpkg --get-selections" and then diff it visually against the output of the same command on a new install of 11.04, I should be able to see all the apps I want to re-install very quickly. 

I really like DAR's capability of doing a _**zipped**_ _incremental_ backup.  Just a few days ago, my 8.10 install went into a state -mysteriously- where the gnome login screen wouldn't recognize my password or the password of any account including root - making it impossible to login.  I had noticed before my last logout that gnome wasn't accepting root password verification when I tried to log out (so I had to simply power down the computer); then there was no way to log in after that ...though all passwords were recognized on a console login (without gnome).  I tried everything that various sources were recommending to fix the gnome problem but without success so I finally had to blow away the install; fortunately I had a recent enough (4 months old) image of the partition.  An incremental Zipped DAR backup of the partition would definitely have been better though.

---

### Post by Bucky Ball on 2011-07-07
If you don't mind having to upgrade your system again by October 2012, go for 11.04. I try to stick to the LTS releases for my production install. 10.04 LTS supported til April 2013, the next LTS, which is due April 2012, will be supported until 2015. LTS releases have support for three years as opposed to eighteen months and upgrade from one to the next can be done with a few clicks in Update Manager. They are generally stabler. 11.04 okay for some, problematic for others (check the forums). 

Good luck whatever you do.

---

### Post by espressoguy on 2011-07-07
> **Bucky Ball said:**
> If you don't mind having to upgrade your system again by October 2012, go for 11.04. I try to stick to the LTS releases for my production install. 10.04 LTS supported til April 2013, the next LTS, which is due April 2012, will be supported until 2015. LTS releases have support for three years as opposed to eighteen months and upgrade from one to the next can be done with a few clicks in Update Manager. They are generally stabler. 11.04 okay for some, problematic for others (check the forums). 

Good luck whatever you do.

Wow, Thanks for speaking up Bucky Ball!!
I don't want to do 10.04 ...had a bad experience with it on my workstation at work.  But if I could just do an "upgrade" from 8.10 to some other release that supports DAR (without having to manually install dependencies), perhaps that would be a good way to go.  Then in April 2012 I could do a fresh install on a wiped-clean partition.  

Is it possible to identify a release that supports DAR and to which I could upgrade in one step from 8.10?

---

### Post by psusi on 2011-07-07
> **espressoguy said:**
> 
Is it possible to identify a release that supports DAR and to which I could upgrade in one step from 8.10?

You can not upgrade 8.10 to anything but 9.04, which also reached end of life some time ago and is no longer supported.

Seeing as how you have been running an unsupported release for a few years which has not had patches to any security vulnerabilities found in that time, there is a fair chance that your system has already been hacked, so you should format and do a clean install anyhow.

If you don't want to run 10.04, then you need to install 11.04 and be prepared to upgrade every 6-12 months.

---

### Post by mörgæs on 2011-07-07
Agree with the post above. 

Now this thread is two days old. A clean install takes one hour.

---

### Post by espressoguy on 2011-07-08
> **An Sanct said:**
> That version is not present any more, if you browse through this directory: [http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dar](http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dar), you will see it has been removed and replaced by a never version (2.3.9 / 2.3.10)

From the list find the version, that suites your architecture and install it from there (the deb package)


I ended up installing the **libdar** and **dar** debs version 2.2.4.  It went in seamlessly and seems to be working well ...it just finished running a rather huge archive.  

Thanks again for the help everyone!  I think this will solve the problem till the next LTS comes out about 9months from now.  A re-install -with all my apps, database, etc will take many hours at that time.

---

### Post by Bucky Ball on 2011-07-08
> **psusi said:**
> If you don't want to run 10.04, then you need to install 11.04 and be prepared to upgrade every 6-12 months.

10.10 more stable, for me at least. I have 10.04, 10.10, 11.04 all booting on this laptop (along with Win7) and I use 10.10 as the stable, production install (soon to be switched to the 10.04 install once sufficiently tweaked!).

ps: esspressoguy: But once you are on an LTS release you'll not have to worry about manually reinstalling again as upgrading to the next LTS is done via the net with a couple of clicks and that updates/upgrades *everything*; installed apps, settings, the works. Takes an hour or two depending on the speed of your connection. The main reason I suggested 10.04 LTS. ;) Good luck with it all and please mark thread as solved if it is. ;)

---

### Post by psusi on 2011-07-08
> **espressoguy said:**
> 
Thanks again for the help everyone!  I think this will solve the problem till the next LTS comes out about 9months from now.  A re-install -with all my apps, database, etc will take many hours at that time.

In the mean time, you are running an OS that is vulnerable to being hacked since it has not been getting updates to fix any of the security vulnerabilities found for over a year now.  Not very advisable.

---

### Post by Bucky Ball on 2011-07-08
> **psusi said:**
> ... You are running an os that is vulnerable to being hacked since it has not been getting updates to fix any of the security vulnerabilities found for over a year now.  Not very advisable.

+1.

---

