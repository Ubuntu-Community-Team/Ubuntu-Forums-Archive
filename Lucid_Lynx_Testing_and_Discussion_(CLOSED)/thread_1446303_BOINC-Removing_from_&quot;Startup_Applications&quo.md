---
title: "BOINC-Removing from &quot;Startup Applications&quot; does not prevent it from running.  Why?"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-04-03
Seti@home 6.03 i686-pc

I don't recall this before.
Anyone know what's changed?

Kill it and it restarts, too!

---

### Post by cariboo on 2010-04-03
Is it started as a service via upstart?

---

### Post by dcstar on 2010-04-03
> **cariboo907 said:**
> Is it started as a service via upstart?

The BOINC daemon always has been a background service.

The Boinc Manager is the only thing that can/should be in the Startup apps.

---

### Post by Didius Falco on 2010-04-03
from the BOINC Wiki:
> 
**Starting BOINC**

 After the installation is finished, the daemon is started  automatically. You can then start the [BOINC Manager]("http://boinc.berkeley.edu/wiki/BOINC_Manager") from the pull-down menu *Applications ->  System Tools -> BOINC Manager*.   The first time you do this you  will be prompted to attach to one or more BOINC projects. 
After the installation is finished the daemon is configured to  start up automatically every time the computer is turned on. You can temporarily disable or re-enable this  by modifying a setting in  the file */etc/default/boinc-client*: 
 # Set this to 1 to enable and to 0 to disable the init script.
ENABLED="1"
At present it seems that you cannot control the BOINC "service" via  the graphical interface, but this may become possible in future releases  of the BOINC software. 


[http://boinc.berkeley.edu/wiki/Installing_BOINC_on_Ubuntu](http://boinc.berkeley.edu/wiki/Installing_BOINC_on_Ubuntu)

More info:

[http://boinc.berkeley.edu/wiki/Stop_or_start_BOINC_daemon_after_boot](http://boinc.berkeley.edu/wiki/Stop_or_start_BOINC_daemon_after_boot)

Regards,

Didius

---

### Post by emarkay on 2010-04-04
Thanks!

---

### Post by Didius Falco on 2010-04-04
you're very welcome!!

---

