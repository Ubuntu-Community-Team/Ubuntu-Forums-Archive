---
title: "[SOLVED] K3B error message"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rbmorse on 2008-10-22
I receive this error message from k3b
> System locale charset is ANSI_X3.4-1968
Your system's locale charset (i.e. the charset used to encode filenames) is set to ANSI_X3.4-1968. It is highly unlikely that this has been done intentionally. Most likely the locale is not set at all. An invalid setting will result in problems when creating data projects.
Solution: To properly set the locale charset make sure the LC_* environment variables are set. Normally the distribution setup tools take care of this.

Any idea of how to fix it?

---

### Post by rbmorse on 2008-10-22
sudo-dpkg-reconfigure locales

---

