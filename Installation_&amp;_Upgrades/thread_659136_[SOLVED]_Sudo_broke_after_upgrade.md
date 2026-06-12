---
title: "[SOLVED] Sudo broke after upgrade"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by perlluver on 2008-01-05
I just upgraded to Hardy, and now when I type in sudo apt-get whatever, it says unable to resolve host.  Is there anyway to fix this?

---

### Post by PmDematagoda on 2008-01-05
Post the results of:-
```
cat /etc/hosts
```
and
```
cat /etc/hostname
```

---

### Post by perlluver on 2008-01-05
This is output from cat /etc/host
```
127.0.0.1 localhost
127.0.1.1 plaufcan.plaufcan

# The following lines are desirable for IPv6 capable hosts
#::1     ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```



this is cat etc/hostname
```
plaufcan
```

---

### Post by PmDematagoda on 2008-01-05
Boot Ubuntu in Recovery Mode, once the booting is complete execute:-
```
startx
```
to start the GUI, after that, execute:-
```
gedit /etc/hostname
```
and change the entry from:-
```
plaufcan
```
to
```
plaufcan.plaufcan
```
After that is done, save the file and then boot back to Ubuntu in normal mode. Your issue should be fixed.

---

### Post by perlluver on 2008-01-05
Going to try that now.

---

### Post by perlluver on 2008-01-05
Thank you very much, that fixed it.

---

### Post by PmDematagoda on 2008-01-05
Glad it worked:), good luck with Ubuntu Hardy development and testing:).

---

