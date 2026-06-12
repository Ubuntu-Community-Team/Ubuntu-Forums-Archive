---
title: "Upgrade from 10.10 to 11.04 fail"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2011-04-28
Fail the upgrading...

> 
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
The package 'update-manager-kde' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

---

### Post by dino99 on 2011-04-28
the servers are actually over charged, so patience or retry in a few days

---

### Post by sephiroth_slash on 2011-04-28
I'm having the same problem, is this really due to servers overload ? or some problem with broken packages ?

---

### Post by jconstantino on 2011-04-28
same problem here...
I don't think this is due to server overload...

see similar error here: 
[https://bugs.launchpad.net/ubuntu/+source/nss/+bug/760713](https://bugs.launchpad.net/ubuntu/+source/nss/+bug/760713)

---

### Post by pwall on 2011-04-29
Ive also got the same problem !

Im running from the australian servers

---

### Post by Lensilvan on 2011-04-29
I had the same problem before I tried to upgrade.

---

### Post by johann_p on 2011-04-29
Same problem here.

---

### Post by sungaMagnus on 2011-04-29
Since I don't use kde, I just remove 'update-manager-kde' and "re-upgrade" and everything seems fine to me.

```
sudo apt-get remove update-manager-kde
```

---

### Post by jiapei100 on 2011-04-30
Thanks man.
works fine for me too.

Thank you again.

Pei

> **sungaMagnus said:**
> Since I don't use kde, I just remove 'update-manager-kde' and "re-upgrade" and everything seems fine to me.

```
sudo apt-get remove update-manager-kde
```

---

### Post by HammerHed on 2011-05-02
Thanks, that worked for me too!

---

### Post by Paul Lynch on 2012-10-18
Worked for me too, now for 12.04 hope I dont regret the upgrade!!!

---

### Post by oldos2er on 2012-10-18
Old thread closed, please don't bump old threads.

---

