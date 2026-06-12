---
title: "Files Owned by &quot;user 1000&quot;; I can't Access"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by Ubuntist on 2010-05-25
Running 9.10 now, I'd like to do a clean install of 10.04 on my dual-boot (with XP) Compaq notebook.  As a test, I burned an ISO image onto a 1-GB stick and booted to 10.04 from it.  It works just fine, except that the directories in the Documents folder on my hard drive are owned by "user 1000", and "he" grants me access to only about half of them.

Is this problem likely to persist if I actually install 10.04 rather than just running it from the stick?  If so, what can I do about it?

Second question: am I correct in understanding that if I still need to access my Ubuntu partition from XP, I'd better stick with ext3 for this install rather than going to ext4?

Thanks, dudes!

---

### Post by John Bean on 2010-05-25
User 1000 is you, or should be on any standard Ubuntu single user installation. type "id -u" in a terminal while logged into your existing installation to confirm this, it should print "1000".

The live CD (or USB in your case) is presumably using some other ID; I haven't checked but using the same id command while logged into the live version will confirm this. However, when you install it the first user created will be 1000, the same as it was when you installed 9.10.

---

### Post by Ubuntist on 2010-05-25
Thanks much!  I'll go ahead in install Lucid.

---

