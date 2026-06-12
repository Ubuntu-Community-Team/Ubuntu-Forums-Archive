---
title: "Can't Load 12.04 Ubuntu Client, Now What"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by ssands10 on 2012-11-27
I have an Acer Aspire Ao751h that ran the netbook version fine. I upgraded to 12.04 and when enter password, I get "Can't Load Ubuntu Client" error message. How do I fix?  I can get to a terminal.  Thank you.

---

### Post by 2F4U on 2012-11-27
If you can get to a terminal, look into the file .xsession-errors in your home folder. Additionally, the system log file may also contain hints on what goes wrong. It may be an issue in the user you are using to logon. Is there another user setup in the system that could be used to see if it is a general problem or just something with a particular user?

---

