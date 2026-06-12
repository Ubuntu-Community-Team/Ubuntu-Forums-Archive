---
title: "gFTP authentication failure."
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2010-03-12
When I try to log in to the FTP server on my ISP subdomain with the Lucid version of gFTP (2.0.19) I get "Authentication failed, sorry."

Using the same password (yes, I've triple-checked I typed it in correctly) in gFTP (same version) in Karmic on another partition on the same machine, I can log in just fine.

As that's the only server I have access to which needs password login, could someone else please try this and see if this is a general problem in Lucid's gFTP or just something odd happening here or at my ISP?

I can't see a relevant bug report on Launchpad.

---

### Post by coffeecat on 2010-03-14
Bump.

Is *no one* using gFTP? :?

---

### Post by coffeecat on 2010-03-21
Bump.

---

### Post by Irihapeti on 2010-03-21
Out of curiosity, I tested gFTP on one of my Lucid installs. I had no difficulty in logging in to a password-protected FTP account.

This particular install is running Openbox. I doubt that it has anything to do with the matter, but I thought it was worth mentioning.

---

### Post by coffeecat on 2010-03-22
Thanks for checking that out. I purged ~/.gftp so that I had to enter all the details again and this time it connected. I guess I must have made a typo in the username (xxx@yyy) which is rather a long one. I had checked that before, but the User field is small and awkward for double-checking a long string.

I'll put this down to user (that's me!) error and mark the thread as solved.

Thanks again.

---

