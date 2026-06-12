---
title: "VMWare Server in repositories"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by veloce on 2007-05-14
I understand that VMWare server is now in the Feisty repositories.  I can't seem to find it, only the kernel modules. Is it really there?

I installed VMWare Server before it was added to the repositories but would like to get upgrades from the repositories. Is there any way to get my system in sync?  Do I have to uninstall vmware and reinstall from the repositories?

---

### Post by jocko on 2007-05-14
It's in the commercial repo. If it's not already there, add this to your /etc/apt/sources.list:
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

---

### Post by veloce on 2007-05-14
Thanks Jocko.  I had (foolishly) assumed that by ticking all the options in Synaptic Package manager that I had added this repository - but no.

I had to uninstall vmware and reinstall (meaning I had to find serial numbers again).

Also, it does the virtual network config without giving me the options to set it up how I want so I had to redo that.

---

### Post by steveneddy on 2007-05-15
OK - I added the commercial repos in my sources.list and installed from Synaptic but it still won't start.

What gives? Any advice or a little hack to get it going?

-SE

---

### Post by veloce on 2007-05-15
> **steveneddy said:**
> OK - I added the commercial repos in my sources.list and installed from Synaptic but it still won't start.

What gives? Any advice or a little hack to get it going?

-SE

Did you enter a serial number during the install?  If not, then you didn't complete the install (this happened to me).  When I re opened Synaptic it told me to run:

```
dpkg --configure -a
```

If that's not the issue, then try running "vmware" from within a terminal. This will either work (which would be unexpected) or it will give an error message which will help work out what is wrong.

---

### Post by jonwatson on 2007-05-24
> **jocko said:**
> It's in the commercial repo. If it's not already there, add this to your /etc/apt/sources.list:
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

Awesome, thanks for the tip!

---

