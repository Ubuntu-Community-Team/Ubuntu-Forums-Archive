---
title: "Sun Java 1.6.0_05 Install Problem..."
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by TenPlus1 on 2008-03-16
I just downloaded jre-6u5-linux-i586.bin and installed it into /usr/lib/jvm/ directory then patched in Opera so it's using the latest version of Java on my system... works fine...

But I tried to set this install as the default java by typing:

update-alternatives --config java

but it only lists the previous java version available which is 1.6.0_03.

Any ideas how to change this ?

Also I tried making a link to the java plugin so that Firefox could use it also, but on replacing the previous link, Firefox refuses to use my new Java install, so I had to re-install the old plugin link...  help Please!

---

### Post by TenPlus1 on 2008-03-16
*phew* ... Thankfully I got the Firefox plugin working ok by doing:

cd /usr/lib/firefox/plugins
ln -s /usr/lib/jvm/jre1.6.0_05/plugin/i386/ns7/libjavaplugin_oji.so
ln -s /usr/lib/jre/jre1.6.0_5/plugin/i386/ns7-gcc29 /libjavaplugin_oji.so 

Yeah.......  Just gotta somehow tell Ubuntu to use the new one as default java...

---

### Post by taurus on 2008-03-16
Maybe

```
sudo cp /usr/lib/jvm/jre1.6.0_05/bin/java /usr/local/bin
sudo update-alternatives --config java
```

---

