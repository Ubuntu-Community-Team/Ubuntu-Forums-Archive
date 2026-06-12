---
title: "Autofs.home and local users"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by bitblit on 2010-06-11
I have my laptop setup with NIS client and autofs so I can login to my work account.  When I'm not connected to my work network, NIS and autofs don't kick in so I can still use my local only account.  However, when I'm connected to my work network and try to login with my local only account, the /home directory is clobbered by autofs so I get a lot of errors regarding missing files.  

I considered moving my networked accounts to /home/networked/*, but I need the paths to remain /home/*.  Is there a way to make autofs mount only /home/<specific directory> rather than clobber the entire /home directory?

auto.master:
```

/misc                  /etc/auto.misc
/net                    -hosts
/home                 yp:auto.home   --timeout=60
/shares               yp:auto.share   --timeout=60
/usr/local/install   yp:auto.local     --timeout=60
+auto.master

```

auto.home
```

*                         server:/ext/users/&

```

---

