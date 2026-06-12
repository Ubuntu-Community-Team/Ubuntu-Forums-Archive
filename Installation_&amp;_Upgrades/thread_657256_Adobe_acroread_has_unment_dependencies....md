---
title: "Adobe acroread has unment dependencies..."
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by Stratis on 2008-01-03
When trying to install acroread I get the following error:

```

stratus@Aladium:~/Third$ sudo aptitude install mozilla-acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  acroread acroread-escript 
The following packages have been kept back:
  ffmpeg 
The following NEW packages will be installed:
  mozilla-acroread 
0 packages upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 31.2MB of archives. After unpacking 78.2MB will be used.
The following packages have unmet dependencies:
  acroread-escript: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
                    Depends: libglib2.0-0 (>= 2.14.0) but 2.12.11-0ubuntu1 is installed.
                    Depends: libgtk2.0-0 (>= 2.12.0) but 2.10.11-0ubuntu3 is installed.
  acroread: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is installed.
            Depends: libglib2.0-0 (>= 2.14.0) but 2.12.11-0ubuntu1 is installed.
            Depends: libgtk2.0-0 (>= 2.12.0) but 2.10.11-0ubuntu3 is installed.
            Depends: libpango1.0-0 (>= 1.18.2) but 1.16.2-0ubuntu1 is installed.
            Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is installed.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

```

I've tried synaptic also to no avail. I've also read more than a few HowTos on the subject in the last hour. 

I'm using Ubuntu 7.10. Can somebody shed some light on to how I might install this?

Thanks!

Stratis

---

### Post by Perfect Storm on 2008-01-03
Tried running update and upgrade and see if it solve the problem?

---

### Post by Stratis on 2008-01-03
> **Artificial Intelligence said:**
> Tried running update and upgrade and see if it solve the problem?

Hey; thanks for the reply. 

It doesn't; I get the same unmet dependencies. 

I was actually able to install the Adobe Acrobat from Adobe's website (in the .deb format), but getting firefox to play with it is an issue. 

I followed a HowTo and added the path to firefox in acrobat's preferences, but it still doesn't register with firefox.

---

### Post by Perfect Storm on 2008-01-04
May I see your sourcelist;
```
cat /etc/apt/sources.list
```
It could be that there's something wrong there, like wrong source.

---

### Post by Stratis on 2008-01-04
> **Artificial Intelligence said:**
> May I see your sourcelist;
```
cat /etc/apt/sources.list
```
It could be that there's something wrong there, like wrong source.

Thanks Artificial Intelligence; it works just fine.

My schools website has a "System Check" that was telling me I had no (compatible) .pdf reader. 

I just tried it out though in firefox and it works just fine. 

It probably expected a Microsoft or Apple product. 

Thanks again! : )

---

