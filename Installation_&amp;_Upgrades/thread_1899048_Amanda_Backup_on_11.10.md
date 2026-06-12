---
title: "Amanda Backup on 11.10"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by mistaWAC on 2011-12-22
So I've got Amanda-Server-3.3.0 amd64 installed on my 11.10 server and am running into a snag.  Every time I run the amdump MyConfig command I'm hit with this error:

```

/usr/bin/perl: symbol lookup error: /usr/local/share/perl/5.8.8/auto/Amanda/Debug/libDebug.so: undefined symbol: Perl_Tstack_sp_ptr

```

Now from what I'm reading online, it seems to be an issue with how Amanda is built (against an old version of perl, 5.8.8, as opposed to a new version, 5.12.4). Has anyone found a solution to this aside from rebuilding Amanda from source against 5.12.4?

---

