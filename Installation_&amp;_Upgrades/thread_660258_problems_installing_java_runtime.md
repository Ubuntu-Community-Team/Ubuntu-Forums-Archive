---
title: "problems installing java runtime"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by boboyo on 2008-01-06
when i got to add/remove programs and i click on java, theres a message that shows up and it says:
This application conflicts with other installed software. To install 'sun-java5-bin' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

when i go to synaptics, this message comes

sun-java5-bin:
 Depends: sun-java5-jre but it is not going to be installed
 Depends: unixodbc  but it is not installable

plz somebody help me!!!

---

### Post by taurus on 2008-01-06
Maybe you don't have all the repos available in /etc/apt/sources.list.  Go back into synaptic again but this time, click the Settings -> Repositories.  Make sure there is a check mark in front of all the lines except the last one, Source code and the CDROM at the bottom window.  Close it and press Refresh.  Now, see if you can install Sun java again.

---

### Post by boboyo on 2008-01-06
thanks alot!!!

that helped me install amsn to!!!

THANK YOU!!!!

---

