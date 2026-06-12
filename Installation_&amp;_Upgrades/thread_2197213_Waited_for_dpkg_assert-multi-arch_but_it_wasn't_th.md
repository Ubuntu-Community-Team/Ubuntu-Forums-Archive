---
title: "Waited for dpkg assert-multi-arch but it wasn't there"
date: 2014-01-02
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2014-01-02
I was attempting to use synaptic to install duplicity...

Error message:
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)

Solution I found some other blog...
 sudo mv /var/lib/dpkg/info/install-info.postinst /var/lib/dpkg/info/install-info.postinst.bad

duplicity seemed to be installed.

---

### Post by pjmlmas on 2014-01-04
I have not tried this solution. I read conflicting solutions. 
Is it dpkg script, xubuntu, synaptic or libc package that has issue.

---

