---
title: "Edgy install: aide broken"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by mswoon on 2006-10-29
apt-get install aide is successful, but it does not work. The following happens on all *three* machines I installed 6.10:

root@toshiba:~# aide
Couldn't open file /tmp/empty/aide.db for reading
root@toshiba:~# aide --init

AIDE, version 0.11a

### AIDE database at /tmp/empty/aide.db.new initialized.

root@toshiba:~# aide --check
Couldn't open file /tmp/empty/aide.db for reading
root@toshiba:~# aide -c /etc/aide/aide.conf --init

AIDE, version 0.11a

### AIDE database at /var/lib/aide/aide.db.new initialized.

root@toshiba:~# aide -c /etc/aide/aide.conf --check
Couldn't open file /var/lib/aide/aide.db for reading

---

