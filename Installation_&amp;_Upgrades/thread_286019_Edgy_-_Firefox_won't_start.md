---
title: "Edgy - Firefox won't start"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by hirev on 2006-10-27
Today when I installed Edgy Eft on my laptop, Firefox will not start up. It just waits to load for abot 5 sec. and disappears.
When I load Firefox through the terminal I get
```
Segmentation fault (core dumped)
```

anyone experienced a problem like this?

---

### Post by Paul Dufresne on 2006-10-27
This has been reported as bug #68137, (no answer yet)
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/68137](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/68137)

---

### Post by Paul Dufresne on 2006-10-27
If you feel like investiging this, you can take a look at:
[https://wiki.ubuntu.com/DebuggingFirefox](https://wiki.ubuntu.com/DebuggingFirefox)

---

### Post by laidbackwebsage on 2006-10-30
Well, the first place someone might want to start is with the fact that the firefox / mozilla firefox executable IS NOT INSTALLED...  ](*,)

As in
:~$ sudo apt-get remove -y  mozilla-firefox && sudo apt-get install -y mozilla-firefox
> Reading package lists... Done
> Building dependency tree
> Reading state information... Done
> ***Package mozilla-firefox is not installed, so not removed***
> 0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
> Reading package lists... Done
> Building dependency tree
> Reading state information... Done
> The following NEW packages will be installed:
>   mozilla-firefox
> 0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
> Need to get 55.9kB of archives.
> After unpacking 115kB of additional disk space will be used.
> Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe mozilla-firefox 2.0+0dfsg-0ubuntu3 [55.9kB]
> Fetched 55.9kB in 1s (31.7kB/s)
> Selecting previously deselected package mozilla-firefox.
> (Reading database ... 218172 files and directories currently installed.)
> Unpacking mozilla-firefox (from .../mozilla-firefox_2.0+0dfsg-0ubuntu3_all.deb) ...
> Setting up mozilla-firefox (2.0+0dfsg-0ubuntu3) ...
:~$ which firefox
:~$ which mozilla-firefox
:~$ sudo updatedb
:~$ locate mozilla-firefox | grep usr | grep -v share | less
> usr/lib/mozilla-firefox
> /usr/lib/mozilla-firefox/plugins
> /usr/lib/mozilla-firefox/plugins/nppdf.so
(END)

Running "locate mozilla-firefox | grep usr | grep -v share | less" produces a long list of files from "/usr/lib/firefox", but the executable isn't there, either...

:twisted:

---

