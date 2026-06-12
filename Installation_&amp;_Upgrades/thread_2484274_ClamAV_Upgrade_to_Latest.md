---
title: "ClamAV Upgrade to Latest"
date: 2023-02-21
forum: Installation &amp; Upgrades
---

### Post by dgzagm on 2023-02-21
Hello All!
When will Ubuntu push out new versions of ClamAV?  How often does this happen?

I have an email server with ClamAV 103.6, however ClamAV has recently upgraded to 103.8 to squash some [vulnerabilities]("https://blog.clamav.net/2023/02/clamav-01038-01052-and-101-patch.html").
 
Package clamav
  
[LIST]
[*][focal (20.04LTS)]("https://packages.ubuntu.com/focal/clamav") (utils):     anti-virus utility for Unix - command-line interface            
0.103.6+dfsg-0ubuntu0.20.04.1 [**security**]: amd64            
0.102.2+dfsg-2ubuntu1 [**ports**]: arm64 armhf ppc64el s390x 
[/LIST]

I believe I can uninstall and install from source, but Ubuntu packages are super nice and easy!  

Thanks,
Dan

---

### Post by ian-weisser on 2023-02-21
New releases occur only with new releases of Ubuntu, or under special circumstances (this probably isn't special).
Instead, each vulnerability is patched, and a new package of the older release is sent through the Ubuntu repositories. Foo-1.3 is replaced by Foo-1.3Ubuntu1
The reasons for this have been well-published for 17 years, so I won't repeat them here. They are easily available if you are interested.

1. Your link to the [ClamAV announcement]("https://blog.clamav.net/2023/02/clamav-01038-01052-and-101-patch.html") lists two CVEs. Note them.
2. Check each CVE against the [Ubuntu CVE Tracker]("https://ubuntu.com/security/cves") to find out which package includes mitigation for your release of Ubuntu,

You will find that despite ClamAV's claim of "critical," this is unlikely to meet the Ubuntu Security Team's definition of "critical," so triage has --as of this writing-- not yet taken place, and the patching work has not yet been prioritized. Be patient and check the CVE tracker periodically.

In the meantime, if you read the ClamAV announcement, you will discover that you should exercise additional precautions if you are scanning HFS+ filesystems or DMG images...neither of which are common in Ubuntu (which is why this seems neither special nor critical).

Folks who are interested in details of the Ubuntu Security Team's workflow and processes should try a few episodes of the [Ubuntu Security Podcast]("https://ubuntusecuritypodcast.org/"). It clears up a lot of confusion.

---

### Post by dgzagm on 2023-02-21
This is a brilliant reply to my post; answers my question and more!  Thank you so much for this info.
Dan

---

