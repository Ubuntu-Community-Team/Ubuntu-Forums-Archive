---
title: "Firefox"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by 3dmatrix on 2008-11-30
I had uninstalled flash pluging through synaptec. On realizing the mistake i tried many times to install flash-nofree and acrobat flash but non of them worked. Finally i uninstalled firefox and reinstalled it. but even that didnt work. So i finally downloaded firefox and flash from their respective websites and installed them (unzip and copy/paste). It works fine, but i am unable to install java plugin to it. Can any one tell how i could do that. I would also like to make the default browser (instead of the original firefox), how can i do that.

---

### Post by Partyboi2 on 2008-11-30
Try installing ubuntu-restricted-extras for java plugin problem.
To change your default browser you should be able to go to System>Pref>Prefered Applications and select "custom" then for "command" enter the new one.

---

### Post by 3dmatrix on 2008-12-01
Installed ubuntu-restricted-extras but it didnt work. When i installed java earlier, it worked in the default browser but not in the new firefox. How can i activate java plugin in my new browser ?

---

### Post by ibutho on 2008-12-01
You need to create a symlink from the location of libjavaplugin_oji.so to your firefox plugins directory
```
ls -l /usr/java/default/jre/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/.
```
Make sure the path to Firefox corresponds to your own version of Firefox.

---

### Post by 3dmatrix on 2008-12-01
there is no such file at that location, rather there is one at  /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7  will that work ?

Copy pasted   /usr/lib/gcj-4.2-81/libjcjwebplugin.so   in the firefox pluginn dir and it is working now. Is it a correct thing to do ?

---

### Post by jamesstansell on 2008-12-02
> **3dmatrix said:**
> there is no such file at that location, rather there is one at  /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7  will that work ?

Copy pasted   /usr/lib/gcj-4.2-81/libjcjwebplugin.so   in the firefox pluginn dir and it is working now. Is it a correct thing to do ?

The first one is what ibutho was trying to direct you to.  (Note that the 6u6 jre had some security problems so if you wanted to use the sun-java6-plugin I would recommend getting the 6u7 version.  My guess is that you're on hardy [ubuntu 8.04] so would need to enable the hardy-updates repository.)

The second one - doing the copy is ok, especially since it's working for you.  The gcj plugin isn't recommended very often.  It was re-worked into the icedtea6-plugin which appeared first in ubuntu 8.10 (intrepid) and is probably more suitable for general-purpose browsing than the gcj plugin was.

---

### Post by 3dmatrix on 2008-12-03
Thanx Its working fine but every time an applet loads it asks for a confirmation to do so.

---

### Post by flclvr8780 on 2008-12-03
i upgraded to firefox 3.0 and now i dont have show all history showing anything. if i go to type or click the address bar drop down, its there but i cant view all my history.  any ideas

---

