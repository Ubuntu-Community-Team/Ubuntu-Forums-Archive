---
title: "kde does not have OFF option in 10.4"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by bunty on 2010-11-21
Hi,

I just updated a system I maintain remotely to kubuntu 10.4 which went pretty well on the whole.

However, having left it running a few days to monitor things the user wanted to power off the machine (an HP laptop)

There no longer seems to be a way to turn it OFF. Apart from the session options there is only suspend and hibernate. 

What happened to OFF ?

TIA.

---

### Post by ankspo71 on 2010-11-22
Hi,
Are you using Ubuntu's original display manager called GDM? GDM is not entirely compatible with the KDE desktop (and vice versa), more specifically GDM will prevent having shutdown and reboot options in KDE. Instead users will have to log out first, then choose to shutdown from the login window. Installing KDM should put these shutdown options right back where they belong in the menu.

If you know that KDM is already installed but it is not in use, then you can use this command to set the default display manager:

```
sudo /usr/sbin/update-alternatives --config x-session-manager
```

Hope this helps.

---

