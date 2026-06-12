---
title: "Cannot receive from Evolution accounts after upgrade to 16.04"
date: 2017-04-05
forum: Installation &amp; Upgrades
---

### Post by Xiguus on 2017-04-05
Hi All,

I have just upgraded my 14.04 partition to 16.04 and can no longer receive mail into my Evolution accounts. Installed version is 3.18.5.2.
Briefly:[INDENT]I launch evolution from a panel icon
mail browser opens
click 'Send/Receive'
login box opens requesting password for principal account
message box pops up showing download activity for additional accounts, 'Complete'
banner message appears over mail browser:[/INDENT]
[INDENT=2]'Error while fetching mail from <secondary account name>
Could not contact <mail.server>: Connection refused'[/INDENT]
I have a backup. Will reloading the backup restore my receive-mail capability, or is there something else I must do?

All assistance greatly appreciated,

Best Regards,

Xiguus.

---

### Post by Xiguus on 2017-04-06
Hi All,

Solution is relatively simple, edit account properties (ie Edit -> Properties) and open tab "Sending e-mail". Tick box "Server requires authentication", Username is address without domain, Close and ready to go.
Question remains, why did this happen?
Not to worry.

Best Regards,

Xiguus.

---

