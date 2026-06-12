---
title: "update error with Hit:1 http://us.archive.ubuntu.com/ubuntu jammy InRelease"
date: 2023-10-23
forum: Installation &amp; Upgrades
---

### Post by dsl2023 on 2023-10-23
hello guys  i have this issue while make update 

how can i fix it !!


```
Hit:1 http://us.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:2 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Hit:3 http://archive.canonical.com/ubuntu jammy InRelease
Hit:4 http://us.archive.ubuntu.com/ubuntu jammy-security InRelease
Hit:5 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.

```


also i have with installing apps



```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  preload
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.5 kB of archives.
After this operation, 94.2 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 preload amd64 0.6.4-5 [29.5 kB]
Fetched 29.5 kB in 3s (9,134 B/s)  
Selecting previously unselected package preload.
(Reading database ... 245459 files and directories currently installed.)
Preparing to unpack .../preload_0.6.4-5_amd64.deb ...
Unpacking preload (0.6.4-5) ...
Setting up preload (0.6.4-5) ...
Processing triggers for man-db (2.10.2-1) ...



```

---

### Post by deadflowr on 2023-10-23
i see no error.

---

### Post by dsl2023 on 2023-10-23
thank you for Reply

so why this hit coming ?

i remember before It wasn't there

but am not sure

---

### Post by dsl2023 on 2023-10-23
guys what about this comment?


#
# Canonical released microcode updates for both Intel (CVE-2022-40982) and AMD
# (CVE-2023-20593). &#8216;Unattended upgrades&#8217; provide security updates by default.
# Ensure it remains enabled to always get all updates as they become available.
#

coming with upgrade it's normal?

---

### Post by deadflowr on 2023-10-23
A basic of what hit get and ign mean in terms of apt/apt-get
[https://askubuntu.com/questions/294525/what-does-ign-get-or-hit-mean-when-running-an-apt-get-update]("https://askubuntu.com/questions/294525/what-does-ign-get-or-hit-mean-when-running-an-apt-get-update")

---

### Post by dsl2023 on 2023-10-23
thank you for clarification

---

### Post by MAFoElffen on 2023-10-23
+1 -- Normal. I saw it updated just fine. Sometimes, on the repo's, it does get a Get Error when the are syncing repo's, but I just try again later and it works.

Security updates for CVE's may get updated or backported, but some do need Ubuntu Pro for older releases. I usually look up what the Ubuntu CVE pages say themselves:
[CVE-2022-40982]("https://ubuntu.com/security/CVE-2022-40982")
[CVE-2023-20593]("https://ubuntu.com/security/CVE-2023-20593")

This is the CVE Reports page for all CVE's: [https://ubuntu.com/security/cves](https://ubuntu.com/security/cves)

See where on that page:
> 
*"Canonical keeps track of all CVEs affecting Ubuntu, and releases a [security notice]("https://ubuntu.com/security/notices") when an issue is fixed."*


I "choose" to do all my update patches manually, and I keep up with them. Maybe that is just how I manage my OCD tendencies.

---

### Post by #&amp;thj^% on 2023-10-23
> **MAFoElffen said:**
> 
I "choose" to do all my update patches manually, and I keep up with them. Maybe that is just how I manage my OCD tendencies.

Same here. ;)

---

### Post by deadflowr on 2023-10-23
> **dsl2023 said:**
> guys what about this comment?


#
# Canonical released microcode updates for both Intel (CVE-2022-40982) and AMD
# (CVE-2023-20593). ‘Unattended upgrades’ provide security updates by default.
# Ensure it remains enabled to always get all updates as they become available.
#

coming with upgrade it's normal?

This is apt news, a new feature(?),  i guess.
to turn off run
```
sudo pro config set apt_news=false
```

---

### Post by dsl2023 on 2023-10-24
Thank you bro it's worked =d>

---

