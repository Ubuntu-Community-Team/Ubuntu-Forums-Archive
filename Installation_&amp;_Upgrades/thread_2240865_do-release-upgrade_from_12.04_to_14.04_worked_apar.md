---
title: "do-release-upgrade from 12.04 to 14.04 worked apart from postfix is broken"
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by bill.damage on 2014-08-22
I did do-release-upgrade and followed all the prompts the best I could, the server rebooted and signs on as 14.4, apache starts and all looks well until I try to collect pop3 mail with thunderbird and it says "Sending of password did not succeed. Mail server responded: Internal error occurred, Refer to server log for more information". Wierd thing is, *sending* with thunderbird is ok. Also, if I try to collect pop3 mail from virtualmin I get the same internal error message where before it was fine. var/log/mail.log hasn't changed since the upgrade, which is very suspicious also.

Anyone seen this before please? I get the feeling this is a quick config fix somewhere, but am stumped were to look. Thanks.

---

