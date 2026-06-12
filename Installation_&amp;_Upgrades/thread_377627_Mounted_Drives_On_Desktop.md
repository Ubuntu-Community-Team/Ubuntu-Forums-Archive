---
title: "Mounted Drives On Desktop"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by dgore on 2007-03-06
Just installed Ubunta 6.10.  I have actually installed twice.  The second time all of my NTFS drives mounted automatically.  Didn't see this happen the first time.  

Now all mounted drives are on my Desktop.  I am glad they mounted but don't really want all of them showing on Desktop.  Is there a way to turn this off.

Thanks

---

### Post by Ek0nomik on 2007-03-06
Terminal:

```
$gconf-editor
```

Then go to Apps->Nautilus->Desktop

Cheers!

---

