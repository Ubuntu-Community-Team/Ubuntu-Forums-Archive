---
title: "/tmp: how to disable auto-cleaning"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by rainer198 on 2005-09-08
Hi everybody,

I am used to employing the /tmp directory for some tasks,
for instance: p2p-shared-folder or temp files when programming.

However, in contrast to my previously installed SuSE,
the tmp-content is deleted after each reboot.

How can I disable this cleaning process?

Thanks a lot,
Rainer.

---

### Post by rainer198 on 2005-09-08
Found it out myself in the meantime.

The cleaning is done by
/etc/init.d/bootclean.sh

No cleaning is done if a variable TMPTIME is negative or infinite.
TMPTIME is set in /etc/default/rcS

I have changed the following line in /etc/default/rcS:
TMPTIME=0
to
TMPTIME=-1

Rainer.

---

### Post by skoal on 2005-09-08
'been meaning to get around to doing the same myself...

thanks for the info.

\\//_

---

