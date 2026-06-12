---
title: "fresh feisty install apt-get broken"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by honeydew on 2007-04-14
I did a fresh install of feisty beta this morning,  I went to upgrade and apt-get complained of broken packages and then offered the suggestion of sudo apt-get install -f.. I posted how it went.. it didnt go very well, any ideas??
```
an:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libdebconfclient0 libdebian-installer4 libdiscover1 libfuse2 libntfs9 xfsprogs
0 upgraded, 0 newly installed, 6 to remove and 337 not upgraded.
6 not fully installed or removed.
Need to get 0B of archives.
After unpacking 4481kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 86571 files and directories currently installed.)
Removing libdebconfclient0 ...
/bin/sh: Can't open ldconfig
dpkg: error processing libdebconfclient0 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libdebian-installer4 ...
/bin/sh: Can't open ldconfig
dpkg: error processing libdebian-installer4 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libdiscover1 ...
/bin/sh: Can't open ldconfig
dpkg: error processing libdiscover1 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libfuse2 ...
/bin/sh: Can't open ldconfig
dpkg: error processing libfuse2 (--remove):
 subprocess post-removal script returned error exit status 2
Removing libntfs9 ...
/bin/sh: Can't open ldconfig
dpkg: error processing libntfs9 (--remove):
 subprocess post-removal script returned error exit status 2
Removing xfsprogs ...
/bin/sh: Can't open ldconfig
dpkg: error processing xfsprogs (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 libdebconfclient0
 libdebian-installer4
 libdiscover1
 libfuse2
 libntfs9
 xfsprogs
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by bulldog on 2007-04-14
If possible,open your synaptic and choose the option  Fix Broken Packages under the EDIT tab.
Maybe it can fix your problems.

After that it could be wise to reload synaptic and set mark all upgrades and finally apply.

---

### Post by honeydew on 2007-04-14
I recieved this as a error...  I think that option in synaptic does the same as sudo apt-get install -f , any more ideas?

```

E: libdebconfclient0: subprocess post-removal script returned error exit status 2
E: libdebian-installer4: subprocess post-removal script returned error exit status 2
E: libdiscover1: subprocess post-removal script returned error exit status 2
E: libfuse2: subprocess post-removal script returned error exit status 2
E: libntfs9: subprocess post-removal script returned error exit status 2
E: xfsprogs: subprocess post-removal script returned error exit status 2


```

---

### Post by bulldog on 2007-04-14
Not really,no.
But a reinstall cost half an hour,and waiting for a useful reply can take hours,so I know what I should do....................:D

---

### Post by honeydew on 2007-04-14
ahh.. so very true..  Ill probably do a fresh install once the final release comes out. this is for personal knowledge as well, because I have never encountered this issue..

---

### Post by tonymccallie on 2007-04-21
I had this exact same problem. I tried a fresh install with the same result. I re-downloaded the iso by torrent and re-installed without a hitch. You might give that a try.

Best of luck, Tony

---

