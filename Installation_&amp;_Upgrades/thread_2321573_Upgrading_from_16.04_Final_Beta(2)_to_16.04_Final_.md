---
title: "Upgrading from 16.04 Final Beta(2) to 16.04 Final release?"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by Christopher on 2016-04-23
I installed the final beta release & was curious if this command would be correct to upgrade now that the final release is available? ** "sudo do-release-upgrade -d"**     Also what command could i use in console to see what version im running now?  Thanks in advance. Chris.

---

### Post by PaulW2U on 2016-04-23
> **Christopher said:**
> I installed the final beta release & was curious if this command would be correct to upgrade now that the final release is available? ** "sudo do-release-upgrade -d"**     Also what command could i use in console to see what version im running now?  Thanks in advance. Chris.
Chris, as soon as you started updating the beta then you were on your way to having the final release. Each update got you that little bit closer. Any alpha or beta release is just a snapshot of development so far and subject to a little more testing than the daily builds.

The following command should show that you've installed the latest updates:
```
lsb_release -a
```
You should see something like this, i.e. "(development branch)" is no longer present :
```
paul@N7110~> lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04 LTS
Release:        16.04
Codename:       xenial
```

---

### Post by Christopher on 2016-04-23
> **PaulW2U said:**
> Chris, as soon as you started updating the beta then you were on your way to having the final release. Each update got you that little bit closer. Any alpha or beta release is just a snapshot of development so far and subject to a little more testing than the daily builds.

You should see something like this, i.e. "(development branch)" is no longer present :
```
paul@N7110~> lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04 LTS
Release:        16.04
Codename:       xenial
```



Yup, thats exactly what i see when i type > lsb_release -a into console.   Thanks much appreciated!  :biggrin:

---

