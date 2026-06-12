---
title: "Is it possible to update older Ubuntu versions?"
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by chiques on 2011-09-10
At the time that 11.04 is the latest version, I need to install 8.04 because I'm working with microcontroller IDE's and toolchains that only support legacy versions. My question:

When I go to update the repositories and binaries, I get error messages. Is it still possible to upgrade my Ubuntu 8.04 up to the last packages before support was dropped? 


Thanks for any help.

---

### Post by Cheesemill on 2011-09-10
Just edit /etc/apt/sources.list and replace all instances of archive.ubuntu.com (may be slightly different in your case) with old-releases.ubuntu.com

---

### Post by chiques on 2011-09-11
> **Cheesemill said:**
> Just edit /etc/apt/sources.list and replace all instances of archive.ubuntu.com (may be slightly different in your case) with old-releases.ubuntu.com

That worked great for my standard repositories. 

I still get errors with the security repositories though

**deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security man restriced**

---

