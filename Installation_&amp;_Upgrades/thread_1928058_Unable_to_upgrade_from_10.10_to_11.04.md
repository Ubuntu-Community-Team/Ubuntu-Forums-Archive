---
title: "Unable to upgrade from 10.10 to 11.04"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by kaleem11 on 2012-02-19
i'm trying to upgrade from ubuntu 10.10 to 11.04 from upgrade manager, each time i face a error saying "
Authenticating the upgrade failed. There may be a problem with the network or with the server. "
with should i do?
and i need a software to create whole system backup. can some 1 help. i'm new to ubuntu.

---

### Post by 2F4U on 2012-02-19
What mirror are you using? Maybe it is down or has other problems. You can change the mirror in the package manager and try again.

---

### Post by kaleem11 on 2012-02-20
and how to change mirror? please guide me. i'm very new to ubuntu.

---

### Post by kaleem11 on 2012-02-20
also tell about backup software.

---

### Post by trimmer on 2012-02-22
Try these and see if it helps.

```
gpg --keyserver keyserver.ubuntu.com --recv 437D05B5

gpg --export --armor 437D05B5 | apt-key add -
```

---

### Post by kaleem11 on 2012-02-28
i went for a clean install by downloading 11.04 iso and making a live usb. thanks for ur support..

---

