---
title: "Ettercap - libpcap.so.0.8 problem"
date: 2012-02-24
forum: Installation &amp; Upgrades
---

### Post by Hellageddon on 2012-02-24
I installed ettercap by using these .deb-packs
```

ettercap-gtk_0.7.3-1.4ubuntu1drizzt1_i386.deb
ettercap-common_0.7.3-1.4ubuntu1drizzt1_i386.deb

```
with the command 
```
#dpkg -i --force-architecture 0-ettercap-gtk_0.7.3-1.4ubuntu1drizzt1_i386.deb
#dpkg -i --force-architecture 0-ettercap-common_0.7.3-1.4ubuntu1drizzt1_i386.deb
```

Ettercap seems to be installed, now. *#whereis ettercap* gives me:
```
ettercap: /usr/sbin/ettercap /usr/lib/ettercap /usr/lib64/ettercap /usr/share/ettercap /usr/share/man/man8/ettercap.8.gz
```

but when I try to launch ettercap I get:
```

#ettercap
ettercap: error while loading shared libraries: libpcap.so.0.8: cannot open shared object file: No such file or directory

```

FYI I use Backtrack 5.1.

---

### Post by Hellageddon on 2012-02-25
Bump

---

### Post by baumanno on 2012-02-25
Hellageddon,

try
# sudo /sbin/ldconfig
# sudo updatedb

worked a treat for me...

[courtesy of [-->link]("http://www.linuxquestions.org/questions/linux-software-2/honeyd-error-while-loading-shared-libraries-libdnet-1-cannot-open-shared-object-fi-885653/") ]

cheers

---

### Post by Hellageddon on 2012-02-26
Didn't really help. Ettercap freezes after a host-scan.

---

