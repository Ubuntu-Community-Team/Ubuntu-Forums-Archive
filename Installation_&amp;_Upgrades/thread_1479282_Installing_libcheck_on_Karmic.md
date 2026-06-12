---
title: "Installing libcheck on Karmic"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by Zubair Ahmed on 2010-05-10
Hi
I am trying to build gnu-pdf library from source. When I run configure script it complains:

"The following required libraries are too old:
   libcheck (svn required)"

Initially configure complained of not finding "libcheck". Then I installed package "check".
Google says there is nothing like "libcheck*" for Ubuntu except libcheck-isa-perl which doesn't help.

Thanks
Zubair

---

### Post by manish.mohania on 2010-06-19
Hi,

Though this reply is too late but still it might help others.

I was also having the same problem. I had to obtain "check" from this location:

svn co [https://check.svn.sourceforge.net/svnroot/check/trunk](https://check.svn.sourceforge.net/svnroot/check/trunk) check

You need to have svn installed on your system.

You will find information about "check" here:

 [http://check.sf.net]("http://check.sf.net/")

You might also find this link to "pdf-devel-gnu mailing list message" useful:

[http://osdir.com/ml/pdf-devel-gnu/2010-03/msg00021.html](http://osdir.com/ml/pdf-devel-gnu/2010-03/msg00021.html)


~ Manish Mohania

---

