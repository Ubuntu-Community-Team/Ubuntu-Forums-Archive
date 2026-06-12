---
title: "Ubuntu 24.04 no synaptic"
date: 2024-04-26
forum: Installation &amp; Upgrades
---

### Post by hakelm on 2024-04-26
Trying to install synaptic on a brand new Ubuntu 24.04 with
apt install synaptic
I get synaptic has no installation candidate.
What can I do?

---

### Post by makitso on 2024-04-26
Did you do an sudo apt update first?

---

### Post by barmak2 on 2024-04-26
Install thru the App Center

---

### Post by hakelm on 2024-04-26
App center says synaptic not found

---

### Post by deadflowr on 2024-04-26
You need to make sure the Community (universe) repository is enabled.
See if it's checked (enabled) in Software and Updates.
If it's not, check it to enable it.

---

### Post by #&amp;thj^% on 2024-04-26
> **deadflowr said:**
> You need to make sure the Community (universe) repository is enabled.
See if it's checked (enabled) in Software and Updates.
If it's not, check it to enable it.
+1
```
apt policy synaptic
synaptic:
  Installed: 0.91.3build4
  Candidate: 0.91.3build4
  Version table:
 *** 0.91.3build4 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Dennis N on 2024-04-26
> **hakelm said:**
> App center says synaptic not found

The thing about App Center is that it defaults to display snap packages only. See screenshot. But the .deb package is also in there: Change "Filter by" setting to "Debian Packages" and it will show up.

---

### Post by hakelm on 2024-04-27
sources.list.d was bungled.
Sorry about that

---

