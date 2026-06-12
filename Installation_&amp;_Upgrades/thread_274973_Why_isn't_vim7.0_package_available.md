---
title: "Why isn't vim7.0 package available ?"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by mdh on 2006-10-10
Hi folks,

Looks like vim7.0 was released in May 2006. I have a vim 6.4 installed on my ubuntu dapper and when I do a apt-get install vim, apt-get tells me that installed vim is the latest version. Is there a specific reason why isn't the vim package upgraded to 7.0 in the repositories?. 

Also I have trouble building vim7.0 from source, when I run 'configure' script from the vim source distribution directory, it exits with the following error message
```
no terminal library found
checking for tgetent()... configure: error: NOT FOUND!
      You need to install a terminal library; for example ncurses.
      Or specify the name of the library with --with-tlib.
```
 
Now, I tried doing a apt-get install ncurses and apt-get complains saying:

```
Package ncurses is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ncurses has no installation candidate
```

Can somebody help me with this installation.

---

### Post by Jussi Kukkonen on 2006-10-10
> Is there a specific reason why isn't the vim package upgraded to 7.0 in the repositories?.
Yes. Upstream version freeze for Dapper was in January and total feature freeze in February. After that (or this is the theory at least) only bugfixes are allowed in. After the release only security fixes and very important bug fixes are allowed, definitely no new versions. If you want to stay more current, upgrade to a development version of Ubuntu.

You can also try to install the .deb package for Ubuntu 6.10 from packages.ubuntu.com, but that might require quite a few packages,

You were probably looking for ncurses-bin, by the way.

---

### Post by mdh on 2006-10-11
Thanks Jussi. But, I am skeptical about installing the development version of ubuntu because my machine is in a production environment. However,I was able to build vim7.0 and the package that was holding me back was libncurses5-dev.

---

