---
title: "E: GPG error: ... The following signaturess were invalid: NODATA 1 NODATA 2"
date: 2012-08-13
forum: Installation &amp; Upgrades
---

### Post by unco on 2012-08-13
Hi, I've been struggling to find an answer to the an apt-get update problem I am having behind a NTLM proxy for a couple of days.

Any suggestions appreciated.

```
sudo apt-get update
...
Get:5 http://nz.archive.ubuntu.com precise-security Release.gpg [4,864 B]
Hit http://extras.ubuntu.com precise/main i386 Packages
Get:6 http://nz.archive.ubuntu.com precise Release [49.6 kB]
Ign http://nz.archive.ubuntu.com precise Release                         
E: GPG error: http://nz.archive.ubuntu.com precise Release: The following signatures were invalid: NODATA 1 NODATA 2
```

Looks like Get 5 worked even though Get 6 fails.

I have Ubuntu 12:04 64. Fresh install which I have repeated a number of time.

I then set up cntlm to handle NTLM proxy. Which I believe is working.

```
cntlm -v -M http://www.google.com
...
	 Response: '62E0E66CC930924BBECC759627780D8EC6237B3267458B6B' (24)
HEAD: HTTP/1.1 302 Found
OK (HTTP code: 302)
...

```

This post is from firefox on the affected machine.  So know I can get thru the proxy to the web from this machine.  And the cntlm results above indicate this also.

I can't figure out what is causing the problem.  Proxy?  Corporate web filter software? ???

I've try lots like below and much more like partial updates ...
```
sudo rm /var/lib/apt/lists/* -vrf
sudo apt-get clean
sudo apt-get update
```

It make no sense to me as my old Xubuntu 10.04 machine after adding proxy configure settings has worked fine for years with apt-get update and the proxy.

Cheers.

---

### Post by unco on 2012-08-13
I have also been given Squid proxy with no authentication and I am getting the same problem.  So has to be something to do with signatures ???

E: GPG error: [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

---

### Post by unco on 2012-08-14
Tried Squid again and it worked so must have been internet connection issues for squid and am guessing it is a cache or timeout on the ntlm proxy.

All going now!  yay.

---

