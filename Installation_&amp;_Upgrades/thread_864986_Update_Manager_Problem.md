---
title: "Update Manager Problem"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by gtg on 2008-07-20
The automatic Update Manager for Hardy has been working fine ... until this week's batch of updates.  Most of the updates went through without a problem; however, when it attempted to download gtkhtml2.14 and libgtkhtml2.14-19, an error occurred with the following details:

W: Failed to fetch [http://mirror.cs.umn.edu/ubuntu/pool/main/g/gtkhtml3.14/gtkhtml3.14_3.18.3-0ubuntu1_i386.deb](http://mirror.cs.umn.edu/ubuntu/pool/main/g/gtkhtml3.14/gtkhtml3.14_3.18.3-0ubuntu1_i386.deb)
  404 Not Found

Any ideas about how to fix this issue would be appreciated.

Thanks.

---

### Post by scragar on 2008-07-20
[http://packages.ubuntu.com/hardy/i386/gtkhtml3.14/download](http://packages.ubuntu.com/hardy/i386/gtkhtml3.14/download)

for the moment use a different mirror to download the package yourself, install by double clicking, entering password if required, then choose install.

As for why your getting an error I have no idea, not even sure what a mod would recommend about reporting this as a bug, since it's technically not ubuntu at fault...

---

### Post by gtg on 2008-07-20
Thanks for the reply.

Going that route (e.g., clicking on the link you provided) first gave me an error (something about a more recent version was already installed).  Then, the Update Manager indicated that more updates were available, so I accepted the proposed updates and everything came through - my system now seems to be up-to-date.

Strange.

---

### Post by coffeecat on 2008-07-20
This happens occasionally when there's a problem with a repository/mirror server. The 404 not found suggests it could be completely down. Use a different mirror as scragar says, or wait a bit and hope that the server has been fixed.

It's Sunday today - you might want to wait until tomorrow. :)

**Edit:** Yup, seen your second post - simultaneous to mine. Seems the server's up again. Someone working overtime? :wink:

---

