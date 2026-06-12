---
title: "Kickstart Post-Installation script."
date: 2015-06-25
forum: Installation &amp; Upgrades
---

### Post by Jason_S._Evans on 2015-06-25
On [https://help.ubuntu.com/lts/installation-guide/amd64/ch04s06.html](https://help.ubuntu.com/lts/installation-guide/amd64/ch04s06.html) I see that "Pre-installation scripts and non-chrooted post-installation scripts may only be shell scripts; other interpreters are not available at this point in the installation."

OK, what I need to know is how to make chrooted post-installation scripts work.  I need it to do two things, wget a script from a webserver and then run that script.  Here's what I have so far:

 ```
# Post Install Script %post --interpreter=/usr/bin/bash --log=/root/ks-post.log
 chvt 4
 exec < /dev/tty4 >  /dev/tty4
 clear


 echo "Downloading ubuntu Post Install - Build 1.0"


 cd /tmp


 /usr/bin/wget -q http://x.x.x.x/physical_provision_scripts/ubuntuscript.sh
 /usr/bin/chmod +x ./ubuntuscript.sh
 /usr/bin/bash ./ubuntuscript.sh


 exec 5>&-
 chvt 1
 %end

```

Any suggestions would be greatly appreciated.

---

