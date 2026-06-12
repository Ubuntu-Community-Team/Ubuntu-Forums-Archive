---
title: "unattended upgrades"
date: 2022-03-15
forum: Installation &amp; Upgrades
---

### Post by sacarde on 2022-03-15
hi,
   in my kubuntu-18.04 I configured unattended.upgrades, and I set in **/etc/apt/apt.conf.d/20auto-upgrades**

```

...
APT:Periodic::AutocleanInterval"0";
...

```

but I dont find pachages upgrade, what I wrong or where should I look?





thank you

---

### Post by ActionParsnip on 2022-03-15
The autoclen interval set to zero means that "apt-get autoclean" won't run. Is the issue that packages are not getting automatically updated here?

---

### Post by sacarde on 2022-03-15
no, the packages are updated correctly, for examples yesterday: 

```

...
Packages that were upgraded:
 libxml2 libxml2-utils python-libxml2
...

```

---

### Post by deadflowr on 2022-03-15
> but I dont find pachages upgrade, what I wrong or where should I look?
What exactly are you trying to look for?

---

### Post by sacarde on 2022-03-15
I am trying to look for packages .deb like into this: [FONT=monospace][COLOR=#000000]/var/cache/apt/archives or similar[/COLOR]
[/FONT]

---

### Post by deadflowr on 2022-03-15
Looks like unattended-upgrades cleans the cache after successful installs by default.
See: [https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1853861]("https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1853861")

---

### Post by sacarde on 2022-03-19
my situation is that updates are applied but *.deb are removed

---

### Post by sacarde on 2022-05-10
[FONT=monospace][COLOR=#000000]**for a possible downgrade**[/COLOR]
[/FONT]

---

### Post by ajgreeny on 2022-05-10
The cache of packages in /var/cache/apt is cleaned up now by default if you install or update using [B][I]sudo apt <> 
[/I][/B]
If you need to keep that cache available you need to use ***sudo apt-get <>***

---

### Post by sacarde on 2022-05-12
can I tell "unattended upgrades" to use apt-get instead of apt?

---

### Post by sacarde on 2022-05-17
the reason is how to downgrade a package after executing "unattended upgrades"


thank you

---

