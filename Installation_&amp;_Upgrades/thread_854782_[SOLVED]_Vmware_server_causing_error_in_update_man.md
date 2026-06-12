---
title: "[SOLVED] Vmware server causing error in update manager"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by paul_5666 on 2008-07-09
hi,

recently, i tried to install vmware server 2 beta on my ubuntu 8.04. but i accidentally downloaded the VERY large rpm package from vmware. seeing my error, i tried to fix it by using alien to convert the package to deb. I then proceeded to installing using the new deb file. The installer went but died halfway. So i went and uninstalled vmware but now my update manager wont let me update telling me there is a broken package, and it wants to fix it but it can't. 

when i click yes in screenshot-1 it comes up with screenshot-2. 

i also get a angry red "no entry" symbol for my package manager on my toolbar at the top.

please help me. i would also like to add that i downloaded the tar package, and installed server 2 and it worked. i just uninstalled it as i think i might try out virtualbox.

should i kill the update manager or reset it somehow?

thanks in advance

---

### Post by Pumalite on 2008-07-09
[http://www.petri.co.il/virtual_install_vmware_server.htm](http://www.petri.co.il/virtual_install_vmware_server.htm)

---

### Post by paul_5666 on 2008-07-09
but thats for windows installation?

or am i missing something

---

### Post by Pumalite on 2008-07-09
[http://pubs.vmware.com/server1/admin/wwhelp/wwhimpl/common/html/wwhelp.htm?context=admin&file=install_gsx.html](http://pubs.vmware.com/server1/admin/wwhelp/wwhimpl/common/html/wwhelp.htm?context=admin&file=install_gsx.html)

---

### Post by paul_5666 on 2008-07-09
xxx:~/Desktop$ rpm -e vmware.rpm
error: package vmware.rpm is not installed


nope doesn't work

---

### Post by paul_5666 on 2008-07-09
argh!
now it ownt let me intall anything with dependancies as it seems the vmware server is blocking the package manager from doing anything? is it possible to reset?

---

### Post by paul_5666 on 2008-07-10
all good
asked and got help in the IRC channel

---

