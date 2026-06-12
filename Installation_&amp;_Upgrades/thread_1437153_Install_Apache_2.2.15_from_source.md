---
title: "Install Apache 2.2.15 from source"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by PeterGriffin on 2010-03-23
Hey guys,

I am new to Ubuntu, I have a Ubuntu 9.10 Server running Apache 2.2.12. I am trying to get it PCI compliant, after running a security scan I am being asked to upgrade Apache to 2.2.15. The latest upgrade from apt-get is 2.2.12, can anyone please help with the upgrade to 2.2.15?

Anyone help will be greatly appreciated.

Thanks.

---

### Post by JoeDaddy717 on 2010-06-21
Was this issue ever resolved?  I am having the same problem.  I was able to upgrade to apache 2.2.14 using repositories and aptitude but cannot figure out the proper way to upgrade to 2.2.15 from source.  I am running Ubuntu 10.04.

Thanks,
Joe

---

### Post by davidmohammed on 2010-06-21
If this is indeed a security issue - the quickest way to get this resolved is to file a bug report on launchpad with the headline "security issue".  If the repository guys concur with you, they will update the repositories and you'll automatically get the latest.

---

### Post by PeterGriffin on 2010-06-21
1

---

### Post by PeterGriffin on 2010-06-21
I did a install of Ubuntu 10.04, and as you said 2.2.15 package was not available.  I was able to pass the scan by hiding all traces of Apache, PCI scan could not tell that I am running Apache and hence did not detect a problem... hehehe  :twisted:

I don't know what was the security issue, because the scan report only told me that "2.2.12 has security issues and I must upgrade to 2.2.15".  At the time, I had to get a passing grade from PCI but I would still like to get the 2.2.15 package or get instructions on how to compile it.

---

