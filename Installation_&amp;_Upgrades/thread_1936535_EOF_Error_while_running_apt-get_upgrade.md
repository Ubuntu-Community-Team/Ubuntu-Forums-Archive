---
title: "EOF Error while running apt-get upgrade"
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by pranavashok on 2012-03-06
I'm running Ubuntu Oneiric (32bit) and I first got this error when running 'apt-get upgrade'. Now I keep getting it whenever I'm trying to run apt and also while opening other programs (gedit, for example).

```
Traceback (most recent call last):
  File "/usr/lib/python2.7/site.py", line 62, in <module>
    import os
  File "/usr/lib/python2.7/os.py", line 49, in <module>
    import posixpath as path
EOFError: EOF read where object expected
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
```

The problematic packages were
```
Errors were encountered while processing:
 /var/cache/apt/archives/python-httplib2_0.7.1-1ubuntu1_all.deb
 /var/cache/apt/archives/python-pkg-resources_0.6.16-1_all.deb
 /var/cache/apt/archives/python-libxml2_2.7.8.dfsg-4ubuntu0.2_i386.deb
 /var/cache/apt/archives/ubuntuone-couch_0.3.0-0ubuntu2_all.deb
```

I tried removing those packages with synaptic and the EOF error repeated.

The complete log of running the 'apt-get -f install' command is [here]("http://pastebin.com/fPxBYfTk")

---

### Post by apemax on 2012-03-06
Hello pranavashok.:)

Have you tried typing in:

```
apt-get update
```

to update apt's package list? Then try:

```
apt-get upgrade
```

---

### Post by pranavashok on 2012-03-06
Yes, those were the first things I tried.

Another thing I did was download Python 2.7 source and copy the site.py and the os.py files into my /usr/lib/python2.7/ directory. Doesn't help.

---

### Post by cortman on 2012-03-06
Looks like this is a bug. I've been googling all over the place, and it most people with the problem don't seem to have a solution.
How difficult would an OS reinstall be...? Painful for a seemingly small thing, but I don't know what else you could do to fix it.

---

