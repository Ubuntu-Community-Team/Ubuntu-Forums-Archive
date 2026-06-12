---
title: "Ubuntu support for cpuid utility - or only Fedora/other linux"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by jenaniston on 2010-02-05
**cpuid** utility is not compiled with U9.04 and the utility is not available as a package with synaptic -
other distributions have it available as rpm . . .

[http://rpmfind.net/linux/rpm2html/search.php?query=cpuid](http://rpmfind.net/linux/rpm2html/search.php?query=cpuid)

Any way to run this utility in the Debian world ?

---

### Post by gmargo on 2010-02-05
If you're wondering about a particular package, **[http://packages.ubuntu.com](http://packages.ubuntu.com)** is an excellent place to look.  This page:

[http://packages.ubuntu.com/search?keywords=cpuid&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=cpuid&searchon=names&suite=jaunty&section=all)

says that cpuid is available and is in the Universe repository which I believe is not enabled by default.

---

### Post by jenaniston on 2010-02-05
> **gmargo said:**
>  cpuid is available and is in the Universe repository which I believe is not enabled by default.

OK - yes . . . Thank you very much.

I did not even check in the *universe* repository. 

i am definitely much more familiar with yumex (Yum Extender) used in Fedora . . .
but now i know that in Ubuntu synaptic package manager when it says **ALL** it is NOT by default including the universe packages.

Very good - thanks again for taking the effort to look it up for me and confirm it is in fact there.

cpuid is supposed to provide some other and different cpu information and parameters than the regular cpuinfo file . . .
so it could be valuable for my laptop fan control troubleshooting.

---

### Post by tguthrie on 2012-04-01
The one from Fedora in RPM form is actually a similar tool, but by a different author.  It is slightly different than the one included in Ubuntu, you can check it out/download a working binary (and source, but not deb packaged) here:

[http://www.etallen.com/cpuid.html](http://www.etallen.com/cpuid.html)

I checked it out, and it seemed to either have more information, or laid out slightly differently.. Which I'm always happy to try new things that may provide a benefit.

A little bit of thread necro, but I figured I would point out the one from Fedora is different, and possibly worth while checking out for anyone else that runs across this thread.

---

