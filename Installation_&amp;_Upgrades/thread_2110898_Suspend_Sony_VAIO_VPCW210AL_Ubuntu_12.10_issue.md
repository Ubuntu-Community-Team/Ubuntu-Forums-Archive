---
title: "Suspend Sony VAIO VPCW210AL Ubuntu 12.10 issue"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by Terraman on 2013-01-31
Hi,

I am using a Sony VAIO VPCW210AL notebook, I just upgraded from Ubuntu 12.04 to Ubuntu 12.10, and suspend is not working anymore. When I suspend from commandline "pm-suspend", suspend doesn't work nor does "s2ram" and neither using tuxonice:

- the screen goes black, but does not turn off
- caps Lock doesn't work
- notebook is on, and doesn't enter suspend mode.

In this state, I can only cut the power off.

I have tried this: **[http://en.opensuse.org/SDB:Suspend_to_RAM#How_to_contact_the_authors_of_s2ram.3F]("http://en.opensuse.org/SDB:Suspend_to_RAM#How_to_contact_the_authors_of_s2ram.3F")**, but I could not make it to work. However, when I boot with "init=/bin/bash" at the boot prompt into a minimal environment work both "pm-suspend" and "s2ram".

I've searched the web, but I could not find out how to solve this issue.

In Ubuntu 12.04 suspend had worked fine.

The out put of "s2ram -i":
```
herman@patricia-laptop:~$ sudo s2ram -i
[sudo] password for herman: 
This machine can be identified by:
    sys_vendor   = "Sony Corporation"
    sys_product  = "VPCW210AL"
    sys_version  = "C1041ZPT"
    bios_version = "R0240E2"
herman@patricia-laptop:~$ 

```

Does anyone know a solution?

---

