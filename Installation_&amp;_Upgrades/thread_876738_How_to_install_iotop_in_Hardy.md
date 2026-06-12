---
title: "How to install iotop in Hardy?"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2008-08-01
I hear iotop is available for intrepid. How can I install it in Hardy? Thanks.

---

### Post by iaculallad on 2008-08-01
> **MountainX said:**
> I hear iotop is available for intrepid. How can I install it in Hardy? Thanks.

System->Administration->Software Sources, click on the "Third Party Software" tab, click on the Add button: input:

> deb [http://ppa.launchpad.net/tormodvolden/ubuntu](http://ppa.launchpad.net/tormodvolden/ubuntu) hardy main

in the Apt Line box. Click Add Source, Click on Close and Reload.

Now, open your terminal and issue the command below to install iotop:

```
sudo apt-get install iotop
```

---

### Post by MountainX on 2008-08-02
that worked perfect :)

---

### Post by tormod on 2008-09-13
You can also install the Intrepid iotop_0.2-2_all.deb package in Hardy without problems. That's why I haven't updated the one in my PPA.

---

### Post by sorochan on 2010-08-10
Be sure to run

gpg --keyserver keyserver.ubuntu.com --recv 4B1E287796DD5C9A; gpg --export --armor 4B1E287796DD5C9A | sudo apt-key add -

after adding the launchpad repo to your sources.list or sources.list.d/launchpad.list

---

