---
title: "installation help"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by ranjithnair on 2008-01-10
I had recently downloaded "**gdesklets**" but it wz depended on "**gdesklets-data**",so I downloaded that too but it wz dependent on "**gdesklets**",in other words both are **interdependent **so I am unable to install it.I dont hav an **internet connection** so I cant install by **synaptic**.

---

### Post by zvacet on 2008-01-10
```
sudo apt-get install gdesklets gdesklets-data
```

---

### Post by ranjithnair on 2008-01-10
For that command, **one requires internet**,I dont hav one.I hav manually downloaded **gdesklets** and **gdesklets-data**.

---

### Post by Partyboi2 on 2008-01-10
what happens when you press on "install package" button? even though it is saying that it requires the installation of 2 packages which are the 2 you are trying to install? I tried without internet connection and it worked for me, as long as you have all the other dependencies sorted for those 2 packages

---

### Post by ranjithnair on 2008-01-11
Thanks for ur help!!But I resolved my problem by using this command

**sudo dpkg -i package1.deb package2.deb ... packageN.deb**

---

### Post by Partyboi2 on 2008-01-11
Glad you got it sorted:)

---

