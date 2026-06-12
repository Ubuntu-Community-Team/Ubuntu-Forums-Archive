---
title: "Could not download the upgrades"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by natron on 2007-10-19
I'm only 8 upgrades away from getting my Gutsy party started and I've received this message
> 
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets-data_2.20.0-0ubuntu1_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets-data_2.20.0-0ubuntu1_all.deb) 404 Not Found
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/r/rss-glx/rss-glx_0.8.1-6ubuntu5_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/r/rss-glx/rss-glx_0.8.1-6ubuntu5_i386.deb) Size mismatch
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib0_0.6.5-0ubuntu16_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib0_0.6.5-0ubuntu16_i386.deb) Size mismatch
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hesiod/libhesiod0_3.0.2-18.1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hesiod/libhesiod0_3.0.2-18.1_i386.deb) Size mismatch
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/z/zephyr/libzephyr3_2.1.20070719.SNAPSHOT-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/z/zephyr/libzephyr3_2.1.20070719.SNAPSHOT-1_i386.deb) Size mismatch
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/n/netbase/netbase_4.29ubuntu2_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/n/netbase/netbase_4.29ubuntu2_all.deb) Size mismatch
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/n/netcat/netcat_1.10-33_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/n/netcat/netcat_1.10-33_i386.deb) Size mismatch
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/lftp/lftp_3.5.11-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/lftp/lftp_3.5.11-1_i386.deb) Size mismatch

I've attempted to partial upgrade 3 times since this warning first showed. The last time was using a different software source. Any ideas?

---

### Post by anubhavrocks on 2007-10-19
try this
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by FredB on 2007-10-19
> **natron said:**
> I'm only 8 upgrades away from getting my Gutsy party started and I've received this message

I've attempted to partial upgrade 3 times since this warning first showed. The last time was using a different software source. Any ideas?

Overwhelmed servers ?

Download an ISO, and try to upgrade from it.

---

### Post by natron on 2007-10-19
> **FredB said:**
> Overwhelmed servers ?
Perhaps that was it, despite the non-indicative error message. My last attempt, as I made my original post, worked. I'm updated and running. Thanks for the replies.

---

