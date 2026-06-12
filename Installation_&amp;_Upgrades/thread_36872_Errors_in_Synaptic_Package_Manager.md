---
title: "Errors in Synaptic Package Manager"
date: 2005-05-25
forum: Installation &amp; Upgrades
---

### Post by cinematography on 2005-05-25
When I go into Synaptic Package Manager, I get the following errors. 

```
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
```

I think some repositories may be missing. :( Does anyone know how I could resore  the missing repositories, or how I could get rid of this error? Any suggestions would be greatly appreciated.

---

### Post by codejunkie on 2005-05-25
i think it's just a server down or having some issues mine's doing the same thing there is nothing you can do to fix it but just wait till it's fixed on ther end or comment that repo out in /etc/apt/sources.list but being that its main repos it would'nt fix anything we still could'nt download anything.

---

### Post by cinematography on 2005-05-25
[QUOTE=codejunkie]i think it's just a server down or having some issues mine's doing the same thing there is nothing you can do to fix it but just wait till it's fixed on ther end or comment that repo out in /etc/apt/sources.list but being that its main repos it would'nt fix anything we still could'nt download anything.[/QUOTE]
Cool. Thank you for your reply.

---

