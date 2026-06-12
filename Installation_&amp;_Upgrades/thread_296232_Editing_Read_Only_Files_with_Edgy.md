---
title: "Editing Read Only Files with Edgy"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by Rick Myers on 2006-11-09
I upgraded to Edgy last night (on my box at home) and found I'm having difficulty modifying read only files. I used to use gksuexec to launch Nautilus, navigate to the file and edit with gedit. Evidently gksuexec is no longer available or was somehow damaged during the upgrade. I've tried "gksu gedit" and "sudo gksu gedit", but I'm still told the file is read only when I try to save. Also tried "gksu vi /path/to/file" and "gksu pico /path/to/file", same read only warnings.

As I write this, perhaps I should just try "sudo gedit"? 

Any help would be appreciated.

---

### Post by ner0tic on 2006-11-09
have you tried gksudo?

---

### Post by Rick Myers on 2006-11-09
> **ner0tic said:**
> have you tried gksudo?

Yes. Same result.

---

### Post by ner0tic on 2006-11-09
who holds the ownership permissions on the readonly file?


ideally, it should just take a simple > gksudo nautilus and just navigate to it.

---

### Post by Rick Myers on 2006-11-09
> **ner0tic said:**
> who holds the ownership permissions on the readonly file?


ideally, it should just take a simple  and just navigate to it.

I'm not at the machine now. I believe owner is root. I'll check when I get home tonight, try your suggestion and post to this thread with additional detail if available.

Thanks!

---

