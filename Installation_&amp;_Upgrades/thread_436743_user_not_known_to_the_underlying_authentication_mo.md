---
title: "user not known to the underlying authentication module"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by timtowle on 2007-05-08
I went through the install process for the previous version and very quickly got to the language screen and partition creation.

With the new version (7.04 feisty fawn) it spewed out lots of error messages for about an hour and then came to a blank screen.

I hit return to receive this message:

"user not known to the underlying authentication module"

---

### Post by ingo on 2007-12-18
I've just had a quick google because I've run into the same problem after creating a live CD. Apparently it is either down to pam or kerberos. Pam has two locations I think, /etc/pam.conf and /etc/pam.d/ - know nothing about kerberos though...

---

