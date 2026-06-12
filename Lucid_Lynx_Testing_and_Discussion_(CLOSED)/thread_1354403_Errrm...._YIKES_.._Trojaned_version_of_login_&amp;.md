---
title: "Errrm.... YIKES .. Trojaned version of login &amp; su."
date: 2009-12-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phillw on 2009-12-13
Hmmm.. ossec. Well, it's doing its job, although I must say I am deeply worried about my last posting from it

> OSSEC HIDS Notification.
2009 Dec 13 21:51:12

Received From: piglet->rootcheck
Rule: 510 fired (level 7) -> "Host-based anomaly detection event (rootcheck)."
Portion of the log(s):

Trojaned version of file '/bin/login' detected. Signature used: 'bash|elite|SucKIT|xlogin|vejeta|porcao|lets_log|sukasuk' (Generic).



 --END OF NOTIFICATION



OSSEC HIDS Notification.
2009 Dec 13 21:51:12

Received From: piglet->rootcheck
Rule: 510 fired (level 7) -> "Host-based anomaly detection event (rootcheck)."
Portion of the log(s):

Trojaned version of file '/bin/su' detected. Signature used: 'bash|/dev/[d-s,abuvxz]|/dev/[A-D]|/dev/[F-Z]|/dev/[0-9]|satori|vejeta|conf\.inv' (Generic).



 --END OF NOTIFICATION



This is a 'clean' partition that has only had 10.04 ever installed on it. I rsynced my ~home over to it, as opposed to mounting my /home partition.

Have there been changes to the two /bin files that ossec does not yet know about - Or, do I have a problem ?

Thanks in advance for any advice.

Regards,

Phill.

---

### Post by phillw on 2009-12-14
From security at ubuntu, c/o canonical

> Shadow 4.1.4.2, from which login and su is built, now gets its default
shell from the build environment, instead of hard coding "/bin/sh". As a
result, the login and su binaries now contain the "/bin/bash" string
instead of "/bin/sh".

The OSSEC HIDS signatures look for the string "bash" in these binaries,
which produces a false positive. The signatures need to be readjusted.

In sum, nothing to worry about.


I just need to teach ossec this new rule.  Nice to report back a false positive - and nicer to know ossec is watching over my system :P

Phill.

---

