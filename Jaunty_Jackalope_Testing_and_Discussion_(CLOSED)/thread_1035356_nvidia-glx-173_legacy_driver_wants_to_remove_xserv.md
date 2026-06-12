---
title: "nvidia-glx-173 legacy driver wants to remove xserver and dependencies"
date: 2009-01-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-01-09
any way around this?

---

### Post by ShirishAg75 on 2009-01-09
Starks are you upgrading from Intrepid to Jaunty or what?

AFAIK Jaunty has that one as well as nvidia-glx-177 and then nvidia-glx-180. 

One of the ways you could try is update the whole index and then do

```
$ sudo apt-get install nvidia-glx-180
```

See if that fixes your issue or not. 

If by doing that you are getting xserver and xorg dependencies out, then filing a bug is in order. 

Btw which xorg and xserver package versions you have. Check them. They should be :-

```

$ apt-cache policy xserver-xorg xorg
xserver-xorg:
  Installed: 1:7.4~5ubuntu10
  Candidate: 1:7.4~5ubuntu10
  Version table:
 *** 1:7.4~5ubuntu10 0
        500 http://archive.ubuntu.com jaunty/main Packages
        100 /var/lib/dpkg/status
xorg:
  Installed: 1:7.4~5ubuntu10
  Candidate: 1:7.4~5ubuntu10
  Version table:
 *** 1:7.4~5ubuntu10 0
        500 http://archive.ubuntu.com jaunty/main Packages
        100 /var/lib/dpkg/status

```

If installed and candidate are both the same then its good, if they are different that means an upgrade is in order.

---

### Post by Ayuthia on 2009-01-09
The only workarounds that I have seen have been to use the nv driver or wait.  Here are a couple of links to discussions about the nvidia driver and xorg:
[http://ubuntuforums.org/showthread.php?t=1034377](http://ubuntuforums.org/showthread.php?t=1034377)
[http://ubuntuforums.org/showthread.php?t=1011847](http://ubuntuforums.org/showthread.php?t=1011847)

---

