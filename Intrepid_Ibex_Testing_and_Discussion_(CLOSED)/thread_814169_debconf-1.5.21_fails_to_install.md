---
title: "debconf-1.5.21 fails to install"
date: 2008-05-31
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rahulthewall3000 on 2008-05-31
```
The following packages will be upgraded:
  debconf
1 upgraded, 0 newly installed, 0 to remove and 406 not upgraded.
Need to get 152kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://archive.ubuntu.com intrepid/main debconf 1.5.21 [152kB]
Fetched 152kB in 0s (538kB/s)
Preconfiguring packages ...
(Reading database ... 128820 files and directories currently installed.)
Preparing to replace debconf 1.5.20 (using .../debconf_1.5.21_all.deb) ...
xargs: xargs.c:443: main: Assertion `bc_ctl.arg_max <= (131072-2048)' failed.
Aborted
dpkg: warning - old pre-removal script returned error exit status 134
dpkg - trying script from the new package instead ...
xargs: xargs.c:443: main: Assertion `bc_ctl.arg_max <= (131072-2048)' failed.
Aborted
dpkg: error processing /var/cache/apt/archives/debconf_1.5.21_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 134
Errors were encountered while processing:
 /var/cache/apt/archives/debconf_1.5.21_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by cariboo on 2008-05-31
Somewhere in this forum there is a solution to this problem, I can't seem to find it right now, so thanks to the author for this solution.

Findutils is the problem so in a terminal type:

```
dpkg -i --force-all /var/cache/apt/archives/findutils_4.4.0-2ubuntu2_amd64.deb
```

of course you will have to use the version that you have in /var/cache/apt/archives.

It worked for me.

Jim

---

### Post by spamzilla on 2008-05-31
Google something like "download debconf-1.5.2**2**" and download / install that file. Then update your sources.list in terminal (sudo aptitude update), open up update manager, untick debconf, and install all other packages. 

That's what I did to get around this problem with no breakage, so maybe it'll work you you :)

---

### Post by Gina on 2008-06-01
The post in question was in another forum - [HERE]("http://ubuntuforums.org/showthread.php?t=783903&page=5") post#46 - I think you'll find (in the Repositories & Backports forum).

> **nivron said:**
> macroshaft,

I had the same exact problem.  I did the following to get past the xargs error:

```
sudo aptitude install findutils
```

After that, I was able to continue along just fine.  Now it's time to see what the next error is going to be. :)

Edit to add - this worked for me and I was able to install all the updates :)

---

### Post by ShirishAg75 on 2008-06-02
I followed Cariboo's advice and it worked, although now it shouldn't be needed as debconf 1.5.22 is also in the repos.

---

### Post by Gina on 2008-06-03
I now have Intrepid running fine on 2 PCs (old desktop and laptop) :)  All ready now for the development testing process.

---

### Post by rahulthewall3000 on 2008-06-07
> **Gina said:**
> The post in question was in another forum - [HERE]("http://ubuntuforums.org/showthread.php?t=783903&page=5") post#46 - I think you'll find (in the Repositories & Backports forum).



Edit to add - this worked for me and I was able to install all the updates :)

Thanks for this Gina, this is what worked for me, even debconf-1.5.22 returned the same error.

---

### Post by Gina on 2008-06-09
Yes, I've found the same thing.  Just built a new PC and installed various versions of Ubuntu on it.  So I now have Intrepid running sucessfully on 3 PCs :)

The latest is an AMD Athlon 64 dual core.

---

