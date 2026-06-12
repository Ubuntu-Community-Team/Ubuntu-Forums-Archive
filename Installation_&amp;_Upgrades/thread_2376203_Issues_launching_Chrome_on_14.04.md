---
title: "Issues launching Chrome on 14.04"
date: 2017-10-31
forum: Installation &amp; Upgrades
---

### Post by jsford892 on 2017-10-31
Hello all,

Let me preface this post by saying I am by no means any sort of pro with Ubuntu or Linux, but I'm not new to it either. At this point though, I have come across an issue that has completely stumped me, so I am coming to the forums for help.

I have a system running Ubuntu 14.04, and this system requires the use of google chrome. As of yesterday I began to encounter the issue of chrome not opening. If you attempt to open it via the GUI nothing happens, and if you attempt to open it via CLI, you get the following: 

```
:~$ google-chrome-stable
[28544:28544:1031/082646.598355:ERROR:edid_parser.cc(181)] invalid EDID: human unreadable char in name
[28544:28582:1031/082646.601005:FATAL:nss_util.cc(632)] NSS_VersionCheck("3.26") failed. NSS >= 3.26 is required. Please upgrade to the latest NSS, and if you still get this error, contact your distribution maintainer.
Aborted (core dumped)



```

After a bit of googling, the general answer seemed to be to reinstall libnss3. If I try to do this, I get the following:

```
:~$ sudo apt install --reinstall  libnss3
[sudo] password for unifi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of libnss3 is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
After doing some research on this, I find that this issue can be cause by broken packages. Most places suggest checking Synaptic for broken packages and then repairing from there, but Synaptic tells me there are 0 broken packages. 

At this point I am completely baffled. Any advice that you guys can offer to help resolve this would be greatly appreciated. Also, if there is any further information needed, please let me know and I will provide it as soon as possible.

Thanks!

---

### Post by TheFu on 2017-10-31
I'd guess there are library dependencies in Chrome that google's build assumed would be there in 14.04.  They may have moved forward, expecting 14.04.5 or 16.04.x to be the oldest releases anyone could run Chrome on.

If you aren't on 14.04.5, might I suggest you upgrade to that release?  To see the version you are running:
```
$ lsb_release -a
```

I won't install chrome on my 14.04 desktop (it is my primary machine still), but chromium (62.0.3202.62-0ubuntu0.14.04.1204) does work fine.  I have libnss3 (2:3.28.4-0ubuntu0.14.04.3).

You can use ```
dpkg -l|grep libnss
``` to see the version on your box.

Hopefully, this will make sense.

---

### Post by jsford892 on 2017-10-31
So I did confirm that this machine is running 14.04.5.

The output from the second command is as follows:
```

$ dpkg -l|grep libnss
ii  libnss-mdns:amd64                                     0.10-6                                              amd64        NSS module for Multicast DNS name resolution
ii  libnss3:amd64                                         2:3.21-0ubuntu0.14.04.2                             amd64        Network Security Service libraries
ii  libnss3-nssdb                                         2:3.21-0ubuntu0.14.04.2                             all          Network Security Security libraries - shared databases

```

So if I am reading this correctly, it does look like I have NSS 3.21. Though, I am not sure what steps I need to take to get 3.26, since I get errors trying to uninstall or reinstall it.

---

### Post by jsford892 on 2017-10-31
A little more digging led me to the following article, which solved my issue:
[https://medium.com/@derrybernicahyady/problem-chrome-doesnt-work-nss-version-check-failed-ce7baec32930](https://medium.com/@derrybernicahyady/problem-chrome-doesnt-work-nss-version-check-failed-ce7baec32930)

Regardless, thank you for your help! setting this to solved! :p

---

### Post by TheFu on 2017-10-31
To maintain an Ubuntu system there are 3 things to do, at least weekly.
* sudo apt update (or use a GUI)
* sudo apt upgrade (or use a GUI)
* Make a versioned backup.  That means you should have 26 backup versions in half a year.

If you forget the 1st, then the second will be useless.  I suspect that was the root issue above, based on the situation you were in.  I perform daily, versioned, backups and weekly patching.  Patching more often than that (or automatic patching) can cause confusion and unwanted issues.

---

