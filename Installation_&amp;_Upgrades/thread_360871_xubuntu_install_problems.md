---
title: "xubuntu install problems"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by CalcProgrammer1 on 2007-02-13
I installed Xubuntu from the alternate CD on a Pentium 133 with 64MB RAM.  It finished, rebooted, and told me to login.  I typed my username and password that I entered at the install prompt, and it failed.  This is a problem, but I can get around it using the Recovery option in GRUB.  However, it didn't install an x server or xfce or anything and i'm stuck in console.  How do I install the interface and get this thing working?

---

### Post by Kateikyoushi on 2007-02-13
In my opinion installing xubuntu-desktop should install it with all it's dependencies I bet X is among them so that should be enough.

```
sudo aptitude install xubuntu-desktop
```

You could reset the password for your user or create a new user.

```
sudo passwd user
```

I think sudo is not necessary in either case because you are running as root.

---

