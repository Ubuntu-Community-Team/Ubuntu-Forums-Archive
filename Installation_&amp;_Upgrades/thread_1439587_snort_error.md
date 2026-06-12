---
title: "snort error"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by Stronghold on 2010-03-26
I'm following an online tutorial to setup snort, which so far has not led me astray, and we get down to actually testing snort, and I get this error; 

> 
 ERROR: Failed to find LibVersion() function in /usr/local/lib/snort_dynamicrules/lib_sfdynamic_example_rule.so: /usr/local/lib/snort_dynamicrules/lib_sfdynamic_example_rule.so: undefined symbol: LibVersion
The tutorial I'm following is; 
[http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10](http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10)

Can anything think of why I'm getting that error?

---

### Post by 2hot6ft2 on 2010-03-26
If I had to guess it's because you're following a tutorial from Mon, 2007-11-19 and was for Ubuntu 7.10 (Gutsy Gibbon) and you haven't said what version of ubuntu you're trying to install it on plus there's a newer version of snort available from: [http://www.snort.org/](http://www.snort.org/).
That combined the fact that 7.10 is no longer supported so the dependencies aren't there to get unless you go and find them (dependency hell).
That version of snort may require an older version of the dependencies than the versions you have by now.

Those could be a few of the reasons.

---

