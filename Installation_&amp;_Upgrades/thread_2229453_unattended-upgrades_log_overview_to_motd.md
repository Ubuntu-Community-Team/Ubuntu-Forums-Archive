---
title: "unattended-upgrades log overview to motd"
date: 2014-06-13
forum: Installation &amp; Upgrades
---

### Post by mina123 on 2014-06-13
I'd like to have unattended upgrades running on my server, but it would still be cool to have easy overview of what is being upgraded. 

Each time I ssh to my server, motd could include something like that:

6 packages were updated: initramfs-tools initramfs-tools-bin libjson-c2 libjson0 libssl1.0.0 openssl
*** System restart required ***

This seems like a good balance between security up-to-date and still finding reasons if something breaks.

I'm guessing it would need separate log file with list of updated packages and .basrc to clear the log when I log in. 
Has anyone made sth like that? Any ideas on implementing it?

---

### Post by bapoumba on 2014-06-15
[https://help.ubuntu.com/14.04/serverguide/automatic-updates.html](https://help.ubuntu.com/14.04/serverguide/automatic-updates.html)
Would the "Notification" section work for you ?

---

