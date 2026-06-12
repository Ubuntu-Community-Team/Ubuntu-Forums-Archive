---
title: "broken repository ?"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by neill on 2007-01-26
hi

i think the 

[http://gb.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-amd64/](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-amd64/)

repository is broken

i can't get synaptic to download the packages.gz file and i can't manually download it either
 (both break at ~42% complete)

anyone else with this problem ?

any workarounds ?

neill

---

### Post by taurus on 2007-01-26
Edit /etc/apt/sources.list and remove **gb** from your repos.

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by neill on 2007-01-26
tried that

so the line in sources.list now reads

http//:archive.ubuntu.com dapper/universe Packages

still hangs !

error reading from server. remote end closed connection [IP 195.248.90.38 80]

:confused:

---

### Post by taurus on 2007-01-26
Remove the : in front of archive.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

p.s.  Can you post the entire /etc/apt/sources.list here?

---

### Post by neill on 2007-01-26
OK

i just tried it again but this time bypassed my firewall/proxy (by plugging straight into the modem) - endian firewall 2.1 (similar to IPCop)

guess what - it worked !!!!!


so ..... now i have to sort the proxy

thanks for your help

neill

---

### Post by taurus on 2007-01-26
[http://www.ubuntuforums.org/showthread.php?t=129843](http://www.ubuntuforums.org/showthread.php?t=129843)

---

### Post by neill on 2007-01-26
not sure why the proxy baulked at that particular repo

the proxy does do 'on the fly' AV scanning - maybe the file was a big on the big side and the server timed out

anyway i know how to do it now if i have to but i will examine the proxy configs and see if i can bypass it for certain IPs

is that given IP in the error message - 195.248.90.38 - fixed for the repo ?

thanks again

neill

---

