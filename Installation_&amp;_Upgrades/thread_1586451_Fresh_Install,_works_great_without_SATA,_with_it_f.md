---
title: "Fresh Install, works great without SATA, with it fails"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by jtdeloach10 on 2010-10-02
So about a month ago, I had a great server. Uptime would be months, and the only downtime would be power related and such, never crashed.

It's OS drive (20 GB ATA) failed, so I immediately ordered a replacement.
And so begin the woes:

I install, it sometimes boots in, others it doesn't. It talks about "uread" and some splash thing on the boot. It never even gives me the username and password (Ubuntu 10.04 Server).

I reinstall, this time boots work, SATA (2 x 1 TB. drives on PCI SATA card one mounted as /home and the other as a movie/tv show drive) do not. I reinstall, hoping to work. And reinstall. And reinstall.

Finally I get tipped off that the "sata_sil" driver is bad. I blacklist it, and I get my present situation.

It is almost identical to the first. I have seen the Data on the harddrives and they mounted correctly and all... then I rebooted. No go since. Can't even log in. I have no idea what to do.


Please help, glad to provide any more detail that is need.

---

