---
title: "upgrade to 9.10 removed glassfish, can't re-install"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by xkaliburx on 2009-12-11
We have upgraded our staging server as a test before production and noticed that glassfish was removed.

The server was running 8.10, was upgraded to 9.04 then to 9.10.  All of the other functions worked fine after the upgrade, ex. apache, bind, etc. but not sure why gf was removed.  An aptitude shows;
i   glassfish-appserv -Open source Java EE 5 Application Server
c   glassfishv2       -Sun's open source GlassFish(TM) v2 Update
c   glassfishv2-bin   -Sun's open source GlassFish(TM) v2 Update

I understand the 'c' shows the config's still exist, but a re-install attempt gives the following;

*apt-get install glassfishv2*
Package glassfishv2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package glassfishv2 has no installation candidate

Does anyone have any suggestions on a different repo or some way to install?

Thanks

---

### Post by charlie cat on 2010-03-28
Apparently glassfish is no longer supported in the repositories as of 9.10.  However, I was able to install glassfish v3 from the official project website, [https://glassfish.dev.java.net/](https://glassfish.dev.java.net/) .  You can also get v2 there if you like.
Here's how I installed v3:
Downloaded [http://download.java.net/glassfish/v3/release/glassfish-v3-web-unix.sh](http://download.java.net/glassfish/v3/release/glassfish-v3-web-unix.sh) into /tmp
Downloaded [http://download.java.net/glassfish/v3/release/glassfish-v3-web.zip](http://download.java.net/glassfish/v3/release/glassfish-v3-web.zip) into /tmp
Opened a terminal (Applications -> Accessories -> Terminal)
Typed:
```

cd /tmp
chmod +x glassfish-v3-web-unix.sh
./glassfish-v3-web-unix.sh

```Then a GUI installer took over.
I'm not completely sure if these filenames and commands are right, I did this several months ago.  If not, you might want to try running the last command under sudo.  I've since started using Apache anyway.

---

