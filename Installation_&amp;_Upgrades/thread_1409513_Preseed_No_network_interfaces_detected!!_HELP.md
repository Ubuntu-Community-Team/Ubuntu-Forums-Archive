---
title: "Preseed: No network interfaces detected!! HELP"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by nikhilt on 2010-02-17
:confused:

I am trying to preseed the UBUNTU 9.04 x86 installer and everything else is okay except that for some systems, it says "No Network Interfaces found" with options as "Continue" and "Go Back".  My network interface detection is set to "auto" in my preseed file. I want to remove this popup. 

Can someone please help with the correct line in preseed.cfg? If there is a better place to ask this pls give me the link.

I've already tried
```
db_fset netcfg/no_interfaces seen true     
```

but doesnt seem to work. Please help!!

---

### Post by newawd on 2010-11-22
Bump?  I am having this exact same problem (only in 10.04), and I've spent a *long* time trying to resolve it.  Can anyone out there tell me how to get past this?

Thanks.

---

