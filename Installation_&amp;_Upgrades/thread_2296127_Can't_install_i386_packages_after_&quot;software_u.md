---
title: "Can't install i386 packages after &quot;software update&quot; in ubuntu 15.04"
date: 2015-09-23
forum: Installation &amp; Upgrades
---

### Post by Quang_Hai_Vu on 2015-09-23
Hi. Today i reinstalled ubuntu 15.04. After install, i try to install software with i386 package (teamviewer_10.0.46203_i386.deb). This package can be installed.
But after software updater (at Dash), i can't install any i386 packages anymore. Sycnaptic package manager show "broken package" and all i386 packages face this issue.

My update config:
- vivid-sercurity
- vivid-updates
- vivid-backports

Please help me :(
Sorry for my bad English :)

---

### Post by TheFu on 2015-09-23
The dependencies for that manually installed .deb file are interfering with normal package management.  
You have a choice to make.

Is your install a i386 or x64 install?  **uname -a** will show us.

---

### Post by Quang_Hai_Vu on 2015-09-23
> **TheFu said:**
> The dependencies for that manually installed .deb file are interfering with normal package management.  
You have a choice to make.

Is your install a i386 or x64 install?  **uname -a** will show us.

Here you are

```
uname -a
Linux TheLegends 3.19.0-28-generic #30-Ubuntu SMP Mon Aug 31 15:52:51 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


```

---

### Post by TheFu on 2015-09-23
Looks like a 64-bit install.  Best to install the 64-bit version of the .deb file.

---

