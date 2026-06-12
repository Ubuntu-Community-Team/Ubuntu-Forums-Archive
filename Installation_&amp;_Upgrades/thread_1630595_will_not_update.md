---
title: "will not update"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by welder663 on 2010-11-25
when i try to update i get an error Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_2.32.0.2-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_2.32.0.2-0ubuntu1_all.deb) 404  Not Found [IP: 91.189.88.30 80] im on a 64 bit hp laptop thanks in advance

---

### Post by pawhtiobo on 2010-11-25
Hi :)

From some reason the Gwibber package is not available from the server, if i where you i would uninstall the current Gwibber software and try the update again. Another option is to try change the main update server, in Synaptic, and see the results.

[IMG]http://bp1.blogger.com/_crimgO_xQv0/R1Rie-4cbZI/AAAAAAAAAjQ/UYVVDrLfX-M/s1600-R/synaptic-software-sources.png[/IMG]

See ya...

---

### Post by sikander3786 on 2010-11-25
> **welder663 said:**
> when i try to update i get an error Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_2.32.0.2-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_2.32.0.2-0ubuntu1_all.deb) 404  Not Found [IP: 91.189.88.30 80] im on a 64 bit hp laptop thanks in advance
Please post the output of

```
cat /etc/apt/sources.list
```

---

### Post by linux-hack on 2010-11-25
Are you behind a proxy ?

---

