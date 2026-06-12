---
title: "Ubuntu 20.04 LTS Requiring ESM (Again)"
date: 2024-05-24
forum: Installation &amp; Upgrades
---

### Post by bpwoods on 2024-05-24
This is not just an up-sale warning, current and active vulnerabilities are NOT being patched in 22.04 LTS!
 
 
 Specifically lets look at this issue (there are multiple):

 [https://ubuntu.com/security/notices/USN-6169-1](https://ubuntu.com/security/notices/USN-6169-1)

 
 
 The patch for gsasl 1.10.0-5ubuntu0.1~esm1 is NOT available to Ubuntu 22.04 even though it is fully supported until Apr 2027 without ESM...  Note that 1.10.0-5 is NOT patched and currently vulnerable.  Only 1.10.0-5ubuntu0.1~esm1 is patched.

 
 
 Please correct me if I am wrong, but right now my security scanners are fairly insistent on this.

---

### Post by deadflowr on 2024-05-24
It's a universe ( community) package not normally supported by Canonical.
Canonical has taken it upon themselves to add support for a select number of community packages.
These packages get that support through the esm system.

ESM stands for extended security maintenance and as such extends support for extra packages and not just for support beyond the normal LTS  5 year support period.

They do this because community supported packages tend to have a rather slow to patch history.

---

### Post by bpwoods on 2024-05-24
Got it.  Thank you for the clarification, can't say I like that, but...  Thank you!

---

