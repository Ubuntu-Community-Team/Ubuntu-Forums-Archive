---
title: "Tomcat installation question"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by ryy705 on 2007-02-06
Hi,
I am trying to modify tomcat installation on ubuntu6.10.  I installed tomcat correctly and I can start it manually from the command prompt.  However I need it to start when the computer boots up.  The instructions in my book say to add a script(provided by the author) to the /etc/init.d directory and install the scripts into the rc.d directory using chkconfig.  

Apparently chkcofig isn't included in ubuntu, so I installed chkconfig, placed the scripts file in the init.d directory and ran chkconfig.  And nothing happened.  chkconfig did not complain, but rebooting the computer doesn't start tomcat automatically.  None of the error messages that should echo out when tomcat does not boot do not show up during system boot either.  So am assuming that the scripts file did not install correctly.  What am I doing wrong?  Kindly help I am new to the linux environment.

---

### Post by deltoya on 2007-02-09
How did you installed tomcat? If you install it through the packaging system (apt-get/synaptic), the start scripts should be added automatically.

Did you download it from tomcat.apache.org?

---

