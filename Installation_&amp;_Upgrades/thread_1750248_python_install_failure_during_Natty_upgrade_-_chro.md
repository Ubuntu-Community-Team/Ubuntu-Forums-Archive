---
title: "python install failure during Natty upgrade - chrooted to try fix"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by mobrien118 on 2011-05-05
Of course, I install Natty successfully on 7 systems, but when it's tie for my server, it fails catastrophically...

During the upgrade, Python failed to install, and now I am left with an inoperable system with 1181 packages left unconfigured.

I'm currently using the installer CD and chrooted into my existing system (with proc linked). The error I get when I try to run ```
dpkg --configure python
``` is ```
Setting up python (2.7.1-0ubuntu5) ...
Linking and byte-compiling packages for runtime python2.7...
file does not exist: /usr/lib/python2.7/dist-packages/aotcompile.py
file does not exist: /usr/lib/python2.7/dist-packages/classfile.py
Errors were ignored.
running python rtupdate hooks for python2.7...
file does not exist: /usr/lib/python2.7/dist-packages/aotcompile.py
file does not exist: /usr/lib/python2.7/dist-packages/classfile.py
pycentral: pycentral updatedefault: error byte-compiling files (3)
```

Any help getting my system back up would be GREATLY appreciated!

Thanks

---

### Post by mobrien118 on 2011-05-10
I'm not normally one to bump a thread, but I've been 5 days without my web server and I'm getting desperate.

Does anyone have any ideas?

I also [posted a bug report in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/python-defaults/+bug/778009") that seems to be getting ignored.

Please, please, if you have any ideas...

---

### Post by sikander3786 on 2011-05-10
Did you try removing Python and reinstalling?

```
sudo apt-get remove --purge python
```

Or

```
sudo apt-get install --reinstall python
```

What does dpkg say about the package.

```
dpkg --status python
```

---

### Post by mobrien118 on 2011-05-10
> **sikander3786 said:**
> Did you try removing Python and reinstalling?

```
sudo apt-get remove --purge python
```

Or

```
sudo apt-get install --reinstall python
```

What does dpkg say about the package.

```
dpkg --status python
```

It took a little bit more than that, but fundamentally, purging the package allowed the rest of the packages to proceed, then re-installing the "ubuntu-desktop" package took care of (most of) the rest, with a little manual intervention here and there.

Anyway, I have never fully grasped the intricacies of the apt package manager, which is why I failed to identify this solution myself, and, thus, why your solution was so helpful.

So, I guess the root cause was that the package was corrupted (during download). Does that sound right?

Thanks so, so much!

--mobrien118

---

### Post by sikander3786 on 2011-05-10
Glad to know it worked for you :-)

And, Most Welcome!

---

