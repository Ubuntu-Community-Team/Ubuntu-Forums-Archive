---
title: "system-config-printer will not accept password"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by gstool on 2007-10-21
I have installed 7.10 from the Live CD.  (Getting the system to boot afterwards was a pain, but that is another story.)

I tried to set one of my printers up using System > Administration > Printing.  All went well until it asked me for my password to authorize the setup.  It would not accept my password.

The only way I could get the printer to install was to use a terminal and execute

sudo system-config-printer, 

entering my same password.  It proceeded without a hitch.

I think the handling of passwords on system administration tasks needs a bit of work.

---

### Post by graabein on 2007-12-30
I can confirm this occurring on Xubuntu 7.10 also. 

Drove me nuts. Going to launch it as sudo in a terminal window now.

---

### Post by steveneddy on 2007-12-30
```

sudo system-config-printer

```

This is the best way at this time to get this done.

---

