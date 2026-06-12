---
title: "Ttranscode package doesn't work: &quot;Broken packages&quot;"
date: 2005-08-16
forum: Installation &amp; Upgrades
---

### Post by Daan on 2005-08-16
I've tried to to install Transcode (so that I can install Tovid) using Synaptic, but it I get errors. Apt-get gives me:

```
daan@Daan:~/unpack/tovid-0.20$ sudo apt-get install transcode
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  transcode: Depends: libavcodeccvs (>= 2:20050427-0.0~5.04ubp1) but it is not going to be installed
             Depends: libfame-0.9 but it is not installable
             Depends: liblame0 (>= 3.96.1-1) but it is not installable
E: Broken packages
```

What can I do?

(Hope I'm in the right forum, not sure).

Thanks!

---

