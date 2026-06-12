---
title: "Location of important configuration files"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by hyapadi on 2005-04-23
I get difficulties in finding the location for the rc.local equivalent. In slackware, I used to use rc.local to automatically run certain command during boot. But I can't find that file in ubuntu. Is there any site reference for location of configuration file in ubuntu?

Thx

---

### Post by alastair on 2005-04-23
The initscripts are all under :

/etc/init.d

With links under /etc/rc*.d

See : [http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-boot](http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-boot)

---

### Post by hyapadi on 2005-04-23
Sorry, but I still confused. In slackware I used to edit /etc/rc.local and add command inside. How should I do it in Ubuntu?

note : the command that I want to run during boot is "sudo wpa_supplicant -B -i ath0 -c /etc/wpa_supplicant.conf -D madwifi -w -dd"


THx

---

### Post by alastair on 2005-04-23
There is no rc.local in Debian, but you can make one yourself.

There is a "skeleton" template : /etc/init.d/skeleton

Copy this to (say) "local" and edit, or make one yourself e.g.

#!/bin/bash
. /lib/lsb/init-functions
log_begin_msg "Running <CMD>  :"
<CMD> 2>&1 > /dev/null
log_end_msg 0

or whatever ....

Then, make the S and K links in /etc/rc* using (for instance) : update-rc.d

See : man update-rc.d

e.g.

sudo update-rc.d <CMD> defaults

---

