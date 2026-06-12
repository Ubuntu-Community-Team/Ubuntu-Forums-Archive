---
title: "Your gdm log files... may contain sensitive info... - Like what?"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-04-05
"Your gdm log files may help developers diagnose the bug, but may contain sensitive information.  Do you want to include these logs in your bug report?"

Never saw this before; notified while Apport-ing a FGLRX issue.

My var/log/gdm  (when accessed via a gksudo Nautilus) shows:
"slave", "greeter" and "log" and "failsafe" logs .

Other than username and a hardware list, what is considered "Sensitive"?

Thanks.

---

### Post by cariboo on 2010-04-05
The username could be considered "sensitive information" as in my case my username is different from the name that is displayed in gdm.

---

### Post by emarkay on 2010-04-05
> **cariboo907 said:**
> The username could be considered "sensitive information" as in my case my username is different from the name that is displayed in gdm.

Yes,  kudos to the Developers for that notice.  Thanks!

---

