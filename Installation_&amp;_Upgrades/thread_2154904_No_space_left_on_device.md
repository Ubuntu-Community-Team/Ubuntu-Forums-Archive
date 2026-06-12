---
title: "No space left on device"
date: 2013-06-16
forum: Installation &amp; Upgrades
---

### Post by Snitz on 2013-06-16
I'm trying to upgrade from 12.04 to 12.10 but something went wrong and I had to do a --configure -a but an error occured once again.

Now I'm getting 

dpkg: error: failed to write status database record about 'libtext-wrapi18n-perl' to '/var/lib/dpkg/status': No space left on device

I cannot do anything until this is resolved.

Thank you.

EDIT: even if I run $sudo dpkg --configure -a I get the following error

dpkg: error: failed to write status database record about 'libgnomekbd7' to '/var/lib/dpkg/status': No space left on device

---

### Post by prodigy_ on 2013-06-16
It usually means what it says. Type ```
df -h
``` in Terminal to check free space.

---

### Post by 2F4U on 2013-06-16
Use df -h to verify which filesystem is full. Then see if you can delete unnecessary stuff. /var and /tmp are usually good candidates to look for obsolete stuff.

---

