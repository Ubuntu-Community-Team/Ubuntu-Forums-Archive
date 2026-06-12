---
title: "Can't browse samba printers"
date: 2009-01-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Bou on 2009-01-28
Hiya,

I'm having this problem where I can't use system-config-printer to browse printers shared via SAMBA. See how the "browse" button appears greyed out.

Are you having this problem, too?

---

### Post by mirhciulica on 2009-01-28
I have the same problem, but didn't have time to investigate it. Also when trying to browse the local network, I don't find any share.

---

### Post by Gina on 2009-01-28
It found the shared printer on the other machine but wouldn't print - kept coming up with Authentication Required but when I entered my password nothing happened and after a while the box came up again.

---

### Post by plun on 2009-01-28
I checked the famous shares-admin and now its impossible to
get permission for changing anything.

So this is for sure a bug......   the shares-admin "bug" has been around since Hardy. 

(Nautilus samba sharing seems to be OK)

---

### Post by Partyboi2 on 2009-02-15
Has anyone found a workaround or opened a bug report about this?

---

### Post by Yes_It's_Me on 2009-02-16
I'm having the same issue. It looks like there are similar launchpa bugs but they are for much older releases, like hardy. Should I report a new bug?

---

### Post by cariboo on 2009-02-16
The browse button is grey out, so I just enter the path to the printer and click forward eg:

```
smb://<workgroup>/<servername>/<printername>
```

You can also add the printer using the cups web interface:

[http://localhost:631](http://localhost:631)

Jim

---

### Post by mariner09 on 2009-02-19
Using the web interface worked for me...

---

