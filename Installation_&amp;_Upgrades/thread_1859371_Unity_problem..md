---
title: "Unity problem."
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by Tuxaby on 2011-10-13
Installed 11.10 upgrade successfully,  Opened Compiz and unchecked Unity and now I have no access to apps, terminal and keyboard shortcuts don't work.  Have a top toolbar with File  Edit  View   Go  Bookmarks  and Help .  No access to shutdown except through ctrl,alt,delete.  Can access system settings right clicking desktop and and clicking "Change Desktop Background" but have no access to compiz.  Any thoughts?  Lee

---

### Post by eliastoon on 2011-10-14
Same issue. Any help?

---

### Post by garvinrick4 on 2011-10-14
> Opened Compiz and unchecked Unity and now I have no access

In terminal (ctrl/alt/t)
```
unity --reset
```

---

### Post by Tuxaby on 2011-10-14
I can't open a terminal.  No access, not hot keys, or any other way.

---

### Post by sikander3786 on 2011-10-14
Please take a look at this troubleshooting guide.

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by e79 on 2011-10-14
> **Tuxaby said:**
> I can't open a terminal.  No access, not hot keys, or any other way.

Does hitting CTRL-ALT-[F2] (actually possibility of F2 to F7) brings you to a TTY where you could type the unity --reset garvinrick4 suggested ?

---

### Post by Tuxaby on 2011-10-14
Thanks e79 that worked.  This forum always comes through.  Many Thanks,  Lee

---

### Post by e79 on 2011-10-14
No problem, I'm glad your issue is solved. Please mark the thread as 'Solved' using the Thread tool if you feel it is complete.

Cheers

---

