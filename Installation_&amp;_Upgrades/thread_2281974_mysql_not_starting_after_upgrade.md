---
title: "mysql not starting after upgrade"
date: 2015-06-11
forum: Installation &amp; Upgrades
---

### Post by mschering on 2015-06-11
Hi,

I just installed the latest upgrades today and noticed mysql couldn't be started anymore. It reported:

Failed to start mysql.service: Unit mysql.service is masked.

I don't know why this happened after the upgrade but in case somebody runs into the same issue you can re-enable it with this command:

systemctl enable mysql

Perhaps it saves someone some time!

Regards,
Merijn

---

