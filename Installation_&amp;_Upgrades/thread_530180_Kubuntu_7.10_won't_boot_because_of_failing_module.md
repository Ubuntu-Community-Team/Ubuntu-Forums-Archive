---
title: "Kubuntu 7.10 won't boot because of failing module"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by martinrandau on 2007-08-20
As the title says, the module - gpsca for the integrated webcam -  keeps the system from booting. 

It hangs after the "Preparing restricted drivers" step with the "usual" gspca-error messages as can be found on the forums.

I have tried to disable the module with gspca.blacklist=yes and gspca_core.blacklist=yes at the boot command line but to no avail.

I am quite pissed off with ubuntu for not fixing the gspca module for acers. I had the same problem with 7.04 and had to use the alternative install cd.

Any help appreciated!

---

### Post by TheWizzard on 2007-08-20
> **martinrandau said:**
> 
I am quite pissed off with ubuntu for not fixing the gspca module for acers. I had the same problem with 7.04 and had to use the alternative install cd.


did you file a bug report?


to boot, use:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_temporarily_skip_boot-up_services](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_temporarily_skip_boot-up_services)

---

### Post by martinrandau on 2007-08-21
Hi and thanks for your reply. I have not filed a bug because I don't really have the time and I think it's there anyway (at least the gspca module not working on some ACERs).

Pressing 'Ctrl+C', as suggested by your link, does not work. 

Is there no way to disable specific modules by the boot options?

---

