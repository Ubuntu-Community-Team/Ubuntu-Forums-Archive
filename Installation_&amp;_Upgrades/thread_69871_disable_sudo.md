---
title: "disable sudo"
date: 2005-09-28
forum: Installation &amp; Upgrades
---

### Post by sadfub on 2005-09-28
I wnat to complete disable the use of sudo, and want to use the old fashioned su, kdesu, ... thing.

therefore one reason:
If someone uses a guest account as normal user and want's to install malware, he just have to know his own password => that really scares me! So if you have 2 passes to know it's a bit harder to hack my box. And I'm not dizzy in which case the pass is required: 1. for my account, 2. for root?

I just want my root password working like it works under debian: With the "sudo passwd..." thing it's not complete cause kdesu doesn't work. Is there a full todo list how I gain a rooted system :-).

Does Updates and such stuff require the sudo thing? So do I have a incompability then?

thanks for replies, I know this seems to be a FAQ, but I've doesn't found any solution on this, every time only how to fix the kdesu thing and the root pass.

---

### Post by frodon on 2005-09-28
When you create a new account, sudo command is disabled by default, you can check that with the property button in System>Administration>user & group.

---

