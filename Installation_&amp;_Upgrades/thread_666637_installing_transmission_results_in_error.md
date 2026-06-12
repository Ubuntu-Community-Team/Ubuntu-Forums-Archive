---
title: "installing transmission results in error"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by KhaaL on 2008-01-13
Hi all, I'm trying to install transmission 1.01 from getdeb, but I end up with this error:

```
khaal@Xeraphim:~$ sudo dpkg -i /home/khaal/Desktop/transmission_1.01-1~getdeb1_i386.deb 
(Reading database ... 179924 files and directories currently installed.)
Preparing to replace transmission 0.93.dfsg-2~gutsy1 (using .../transmission_1.01-1~getdeb1_i386.deb) ...
Unpacking replacement transmission ...
dpkg: error processing /home/khaal/Desktop/transmission_1.01-1~getdeb1_i386.deb (--install):
 trying to overwrite `/usr/bin/transmission-remote', which is also in package transmission-cli
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/khaal/Desktop/transmission_1.01-1~getdeb1_i386.deb

```

Any idea what the culprit could be here?

thanks

---

### Post by taurus on 2008-01-13
Why don't you go into synaptic and remove the transmission on your machine first before you install the latest one from a terminal?

---

### Post by KhaaL on 2008-01-13
That fixed it, the new interface is delicious :p
Thanks!

---

