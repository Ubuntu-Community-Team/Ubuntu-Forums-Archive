---
title: "10periodic vs. 20auto-upgrades"
date: 2015-06-12
forum: Installation &amp; Upgrades
---

### Post by funtomasz on 2015-06-12
Hello Everyone!

I have 10periodic and 20auto-upgrades in /etc/apt/apt.conf.d.

If I correctly understand, 20auto-upgrades replace configuration of 10periodic. Is that right?

My /etc/apt/apt.conf.d/10periodic
```
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::Unattended-Upgrade "1";
APT::Periodic::Update-Package-Lists "1";
```

and my /etc/apt/apt.conf.d/20auto-upgrades
```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";
```

Should I delete one of them? Or it is not necessary to delete?

---

### Post by ian-weisser on 2015-06-12
Do not delete either file. I don't know where you got 20auto-upgrades from, but 10periodic is provided by the package 'update-notifier-common'
Deleting package-provided files is a quick way to break your package manager.

You can change the files all you like, just don't delete them.
It's perfectly fine for multiple apt-conf files to change the same setting. Confusing, perhaps, but not a problem.
Apt will read each file in sequence, changing settings each time like flipping switches. The same setting twice set to '1' keeps it at '1'.

---

