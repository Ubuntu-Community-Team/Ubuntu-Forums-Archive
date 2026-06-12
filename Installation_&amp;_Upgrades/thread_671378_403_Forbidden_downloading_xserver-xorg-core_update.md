---
title: "403 Forbidden downloading xserver-xorg-core update"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by pantherse on 2008-01-18
Hi,

Update Manager is encountering 403 forbidden when downloading xserver-xorg-core update. Here's the error message I'm getting:
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
  403 Forbidden

---

### Post by DarkStarAeon on 2008-01-18
Yeah same here.

All the other updates installed fine, but that xserver-xorg-core update just doesn't want to work.

---

### Post by dasy2k1 on 2008-01-18
ditto here...

not sure what is going on.

---

### Post by Aintaer on 2008-01-18
Confirmed here as well.
Somebody set the wrong privledges or ownership on that package maybe?

---

### Post by Michl on 2008-01-18
Same here, but only on one computer.  Installed to feisty on another one
and to gutsy on my laptop without problems.  Any solutions?

---

### Post by TheDriZZle on 2008-01-18
What could cause this problem? 

I tried clearing the cache and tried restarting the name service, nscd.

Neither of these worked, My friend said he got the ubuntu updates with no problem this morning. What is up with aptitude!

---

### Post by Jeff_C on 2008-01-18
Same issue here too.

---

### Post by kfries6 on 2008-01-18
Sounds like it is a version thing.  I have a Gutsy Ubuntu desktop, which I have not tried to update yet because it is currently hosting about 8 virtual machines.  One of those VMs is has an X desktop and that machine is experiencing this issue.  Here is its details:

Ubuntu Gutsy Jeos 7.10
Getting updates via Apt-Cacher
running xubuntu desktop environment
Exact Error Message:

Failed to fetch [http://LabDC.hermes.internal:3142/security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://LabDC.hermes.internal:3142/security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
  403 Forbidden

---

### Post by p_quarles on 2008-01-18
The package was taken down after it was discovered that it was killing Java apps. Also, there are about 50 other threads on the same issue. ;)

---

### Post by angus_young on 2008-01-18
Yeah having the same problem here, on AMD64 version

---

### Post by JarrodHayes on 2008-01-18
I'm getting the same error.  Anyone know when the package will be put back up?  I was in the middle of a video driver upgrade and now my OS is shot :(  Where can I get a previous version of the package?

---

### Post by OldGrey on 2008-01-18
Same problem

Any answer yet?

---

### Post by kfries6 on 2008-01-18
> **p_quarles said:**
> The package was taken down after it was discovered that it was killing Java apps. Also, there are about 50 other threads on the same issue. ;)

Yea, but so does Compiz, so how did anyone notice
:lolflag:

---

### Post by p_quarles on 2008-01-18
For up-to-date info, take a look at the Launchpad page on the issue:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

---

### Post by Nem1976 on 2008-01-18
I know the file was removed because it was causing issues with Java.  But what would the possibility of when it fails to install give the actual reason.  So the message I got was 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
  403 Forbidden


What about having it say 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
 "Removed  -  then display url to specific forum article"


It would help solve all these posts from being created regarding the same issue.

---

### Post by p_quarles on 2008-01-18
If you read the Launchpad page I linked to, you'll see that they're currently working on the 403 issue as well.

---

### Post by kfries6 on 2008-01-18
> **Nem1976 said:**
> 
What about having it say 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
 "Removed  -  then display url to specific forum article"
.


The file is fetched via wget or curl I forget which.  The 403 is the only information available to the update process.  403 is an HTTP error.  So when the file was taken down, the wget process failed with that message.  To make the process more verbose would require a fairly serious change to the update process.

HTH

---

### Post by Nem1976 on 2008-01-18
> **p_quarles said:**
> If you read the Launchpad page I linked to, you'll see that they're currently working on the 403 issue as well.

Ah very cool lol I guess I need to start monitoring the Launchpad page more often.  
I have been looking but I can't find a Rss feed for just the recent submitted bugs.  I have Ubuntu forums setup on a Rss feed and want to add the Launchpad as well but just for ubuntu submitted bugs anyone have that feed url.?



> **kfries6 said:**
> The file is fetched via wget or curl I forget which.  The 403 is the only information available to the update process.  403 is an HTTP error.  So when the file was taken down, the wget process failed with that message.  To make the process more verbose would require a fairly serious change to the update process.

HTH

Ya very true thanks for the clarification.

---

### Post by AJB2K3 on 2008-01-18
Why doesn't anybody read up on the 403 error when it happens every few months.

[http://www.checkupdown.com/status/E403.html]("http://www.checkupdown.com/status/E403.html")

---

### Post by dgluss on 2008-01-18
Would it be possible to remove the reference to /xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb
that occurs in security.ubuntu.com//ubuntu/dists/gutsy-security/main/binary-i386/Packages
at line 8451?  That would make this problem go away, right?

DG

---

### Post by DrMega on 2008-01-18
The question nobody seems to be asking is this: Are we losing out on anything by not being able to apply the update? I.e. does the update fix a security issue, or a significant bug? Does it give us performance improvements etc?

I'm quite happy with my build as it is at the moment. I regularly apply all available updates but if one won't come down, I just forget about it and let it come down in its own sweet time:)

---

### Post by p_quarles on 2008-01-18
It's a bug fix build. I don't have the specs for the Ubuntu package, but this is what was announced in the Debian Security list:
> 
Several local vulnerabilities have been discovered in the X.Org X
server. The Common Vulnerabilities and Exposures project identifies the
following problems:

CVE-2007-5760

    "regenrecht" discovered that missing input sanitising within
    the XFree86-Misc extension may lead to local privilege escalation.

CVE-2007-5958

    It was discovered that error messages of security policy file
    handling may lead to a minor information leak disclosing the
    existance of files otherwise unaccessible to the user.

CVE-2007-6427

    "regenrecht" discovered that missing input sanitising within
 the XInput-Misc extension may lead to local privilege escalation.
EDIT: So, yes, it's an important update, but the fixed package is being worked on quickly.

---

### Post by dgluss on 2008-01-18
Apparently, all fixed now!

Thanks!

DG

---

### Post by SonicSteve on 2008-01-18
Just to confirm,
I had the same error (as did many I assume), I can download the update now. It installed, don't know about the java errors but all seems well.

EDIT
I had to first check for updates again and the .1 on the end of the update then changed to .2 
Then the update worked.

---

### Post by DarkStarAeon on 2008-01-19
Yeah, same here, I unchecked the box for the update, then checked for new updates, and suddenly the version number went from .1 to .3

Looks like .3 came out this morning. (Sat. 19th)

So, this one doesn't work:
[http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)

This still had issues: 
[http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.2_i386.deb)

This one does work:
[http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.3_i386.deb)

---

