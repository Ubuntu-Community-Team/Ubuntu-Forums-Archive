---
title: "AutoFS mounting CIFS shares read-only"
date: 2009-07-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by scaine on 2009-07-21
On my Jaunty boxes, my central server is available read-write.  However, on my newly installed (from Alpha 2) Karmic box, despite using the same credentials and IP address, all the autofs shares are read-only.

If I "gksudo nautilus", I can write to the shares, so I think it's something specific to the way autofs creates the mount directory (in my case, it's /smb), but despite trying to change the permissions on that directory with autofs stopped, the moment autofs is restarted, the first thing it does is chown the directory back to root again.

Any ideas?

---

