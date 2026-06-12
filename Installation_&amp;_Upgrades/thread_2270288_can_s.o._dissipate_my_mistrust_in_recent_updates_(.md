---
title: "can s.o. dissipate my mistrust in recent updates? (sudo + heimdal related)"
date: 2015-03-21
forum: Installation &amp; Upgrades
---

### Post by bardo2 on 2015-03-21
Hello,

 unfortunately my first question in here might touch difficult grounds, but since it is bothering me seriously, i may need help to get over it.

One week ago, Ubuntu asked me to update (System updates). While i was interested to see, WHAT would get updated to avoid possible breakage of my fragile, yet advanced system (Trusty, gnome, zfs,...), i found (among other packages) package "sudo" waiting to be updated. (from 1.8.9p5-1ubuntu1 to 1.8.9p5-1ubuntu1.1). I know the following information needs better understanding than mine, but - while interested to learn what the change affecting a crucial part of the system might involve - i was surprised to find a link to some failing website only:

CVE-2014-9680 turned up "Unable to load vulnerability."

While i was assuming, that the format change of the vulnerability database might be a possible cause, i was still interested to see, what motivated that change, and was surprised to find a U.S. "National Vulnerability Database" waiting to be allowed admin priviledge on my home PC. Surprised, because ubuntu (just as debian was) still is a community effort (lead by Canonical, a U.K. based company, at best) not obeying US national interests, right?

So i began to read up... - not code, because i read my last piece of code some 20+ years ago and felt unable to be sharp enough - but other material, like what other packages came along with that patch. And there have since been plenty of heimdal related patches (heimdal being a kerberos implementation), to enforce my fear, the sudo change *COULD* be the cornerstone to finish an architectural change, which could be summarized by: Any company controlling the kerberos server (or being registered as priviledged there) would be able to decide upon anything on my PC although they dont know a thing about my configuration/needs/limitations.

I was not willing to allow this to happen (basicaly degrading my hardware into a free lease to those companies and no longer owning it, more like paying for hardware + electricity for their interests).
What i did, was to use a combination of apt-mark and apt-pinning to prevent this update from happening. BUT: While i tried to further examine the effects of the change inside virtual machines, i saw it is around (with different version numbers) in all later ubuntu releases as well. Even worse: When i gave it a try to rip heimdal completely from a working Ubuntu installation, i saw a dependancy hell causing major parts of the system to vanish, rendering the whole installation to be unuseable.

At the end, i feel very much like being the powerless witness of evil changes, introduced by Canonical in the interest of US government, neglecting users interests. Where are my options?

Or do i miss some important point?

---

### Post by grahammechanical on 2015-03-21
You need to be more specific if you are to convince me that upgrading a package to close a vulnerability is some kind of conspiracy by a government agency. To start with, if it is a conspiracy the perpetrators would not leave clues that would lead you to the conspirators.

I would not call this "some failing website."

[http://people.canonical.com/~ubuntu-security/cve/2014/CVE-2014-9680.html](http://people.canonical.com/~ubuntu-security/cve/2014/CVE-2014-9680.html)

Are you basing your claim on this?

[http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-9680](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-9680)

or this?

[https://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-9680](https://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-9680)

So, a government database for recording discovered vulnerabilities in software which is made available to the public is suspect simply because it is a government project? Is that your reasoning? 

 My thinking is to be thankful that I am running a Linux distribution whose main sponsor (Canonical) has procedures in place to keep up to date with reported vulnerabilities and who is quick to update my system with patched software. I am thankful that my Ubuntu system is being protected.

[http://www.ubuntu.com/usn/usn-2533-1/](http://www.ubuntu.com/usn/usn-2533-1/)

We have a weekly Ubuntu news letter which includes information about security updates in Ubuntu. Nothing is being done in secret.

[http://ubuntuforums.org/showthread.php?t=2268568](http://ubuntuforums.org/showthread.php?t=2268568)

Or perhaps this is done to lull us into a false sense of security. What do you think?

---

### Post by bardo2 on 2015-03-21
Thank you for looking into this.
Your link helped me to realize a misconception on my side and to calm down my "*paranoic*" emotions - somewhat...
What a pity, that i received such a negative verdict along with it. BTW: This is the second time (in 4 years) that my "*contributions*" to ubuntuforums were repelled, and it was much faster this time. Fortunately, there are other places on the net, even some welcoming the effort and time, i invested into the plattform. I guess i have to accept some degree of "incompatibility" among this forums rules and my habits, which is very unfortunate.

So i'll take it:
> Goodby.

edit: After your original post got revised... i have to revise mine as well:
Excellent research there! Thank you so much. Yes, you followed my shoesteps without falling into my nightmarish trap. Great relief, good job, man.

---

