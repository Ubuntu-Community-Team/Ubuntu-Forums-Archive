---
title: "Eclipse 3.2 via apt-get?"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by nsoeffers on 2006-07-05
Hello,

i was wondering when eclipse 3.2 (callisto) becomes available via apt-get?
And if it takes a long time. Where you install it? Home dir or /usr/lib/eclipse or /usr/share/eclipse???

Thanks in advance,
Kind regards,

Niels

---

### Post by tonyr on 2006-07-05
There's no way to tell when Eclipse will be available in the repos.  It really depends
on when the Debian Maintainers (pkg-java-maintainers@lists.alioth.debian.org) choose
to make it available.

You an download Callisto and install it anywhere you want to.  Likely candidates
would be **/opt** or **/usr/local**.  The downloaded file  (.bz2 or .gz) has
everything needed).  I installed in my home directory.  The only consideration
is whether you are the only user or you want to make it available to other users
on your computer.

---

### Post by jgruuk on 2006-07-07
> **tonyr said:**
> There's no way to tell when Eclipse will be available in the repos.  It really depends
on when the Debian Maintainers (pkg-java-maintainers@lists.alioth.debian.org) choose
to make it available.

You an download Callisto and install it anywhere you want to.  Likely candidates
would be **/opt** or **/usr/local**.  The downloaded file  (.bz2 or .gz) has
everything needed).  I installed in my home directory.  The only consideration
is whether you are the only user or you want to make it available to other users
on your computer.
Do you know any place that explains clearly what are the differences between installing Eclipse in:

* /opt
* /usr/local
* /usr/share
* /anyotherplaceidontknowof ...

I understand that there's not one answer (to rule them all), what are the best practices for these kind of things?

thank you very much.

---

### Post by tonyr on 2006-07-07
> **jgruuk said:**
> Do you know any place that explains clearly what are the differences between installing Eclipse in:

* /opt
* /usr/local
* /usr/share
* /anyotherplaceidontknowof ...

I understand that there's not one answer (to rule them all), what are the best practices for these kind of things?

thank you very much.

I do not know the answer.

There is a Linux Filesystem Heirarchy Standard document [here]("http://www.pathname.com/fhs/") that 
may answer some of your question.

The eclipse downloads from [http://www.eclipse.org](http://www.eclipse.org) are self-contained.
The Debian packagers (and others?) have apparently chosen to use a 
different installation model by distributing the contents to several
directories in a manner that better fits (my guess here) the Linux 
multi-user environment.

**/usr/share** has a particular use described in the document I 
mentioned, and the Debian package puts **some** of the files there under 
**/usr/share/eclipse**, so choosing that as an installation point
is not a good idea.

---

