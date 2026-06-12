---
title: "Unable to upgrade to Ubuntu 7.10"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by aliov_85 on 2008-07-09
Hi 

I'm on ubuntu 7.40 and I would like to upgrade to ubuntu 7.10.

I get the following error from package manager:

> 
**Getting upgrade prerequisites failed**
The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.


How can I fix this problem?

Thanks in advance

Ali

---

### Post by damis648 on 2008-07-09
> **aliov_85 said:**
> Hi 

I'm on ubuntu 7.40 and I would like to upgrade to ubuntu 7.10.

I get the following error from package manager:



How can I fix this problem?

Thanks in advance

Ali

Are you specifically trying to update to 7.10? 8.04 is out now. Try that.

---

### Post by sharks on 2008-07-09
have u tried this command :

sudo apt-get dist-upgrade

---

### Post by aliov_85 on 2008-07-09
Thanks 

No, not specifically, I thought I should do that in order to upgrade to 8.04, also I think I've update problems.

---

### Post by Sef on 2008-07-09
> No, not specifically, I thought I should do that in order to upgrade to 8.04, also I think I've update problems.

Before upgrading, you should install all the upgrades for your current system.

---

### Post by aliov_85 on 2008-07-09
> **Sef said:**
> Before upgrading, you should install all the upgrades for your current system.

Hi

The problem is that I can't update. When I try to update, it failes.

---

### Post by zvacet on 2008-07-09
```
sudo apt-get update && sudo apt-get upgrade
```

If that doesn´t work 

```
cat /etc/apt/sources.list
```

and post it here.

---

