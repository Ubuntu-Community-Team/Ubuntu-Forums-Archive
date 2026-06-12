---
title: "Firefox 2 and Java"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by Cirdan7 on 2007-01-02
I installed Firefox 2 manually and am trying to get java working on it. I have java installed but it doesn't seem to work in Firefox. I have libjavaplugin.so and libjavaplugin_oji.so in the /opt/firefox/plugins but it doesn't work. ](*,)

---

### Post by bruenig on 2007-01-02
Assuming you had all of the ff 1.5 plugins and you still have that installed and were working, you should be able to do the following.
```
sudo rm /opt/firefox/plugins/*
sudo ln -s /usr/lib/firefox/plugins/* /opt/firefox/plugins
```

---

### Post by Cirdan7 on 2007-01-02
Thanks, but it didn't quite work. I did still have /usr/lib/firefox/plugins, but firefox still doesn't see the lib. Do I need to restart or something? I did close firefox did ps -A to make sure it wasn't runner then opened it again and tried it, but it didn't work.

---

### Post by bruenig on 2007-01-02
If firefox 1.5 works with java, then firefox 2.0 should work with java now as the second command symlinks all the 1.5 plugins. I don't see how it possible could work in 1.5 and not 2.0

---

### Post by Cirdan7 on 2007-01-02
Here is the output from the console

ryan@ryan-laptop:~$ ls /opt/firefox/plugins
flashplayer.xpt    libjavaplugin_oji.so  libnullplugin.so
libflashplayer.so  libjavaplugin.so      libunixprintplugin.so

Also, flash works.

---

### Post by bruenig on 2007-01-03
why do you have two java plugins in there. libjavaplugin.so usually is just symlink to libjavaplugin_oji.so

Do the following and paste the output of each.
```
file /opt/firefox/plugins/libjavaplugin.so
file /etc/alternatives/mozilla-javaplugin.so
ls /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/
```
and
```
file /opt/firefox/plugins/libjavaplugin_oji.so
```

---

### Post by Cirdan7 on 2007-01-03
ok here it is

ryan@ryan-laptop:~/Projects$ file /opt/firefox/plugins/libjavaplugin.so
/opt/firefox/plugins/libjavaplugin.so: symbolic link to `/usr/lib/firefox/plugins/libjavaplugin.so'

ryan@ryan-laptop:~/Projects$ file /etc/alternatives/mozilla-javaplugin.so
/etc/alternatives/mozilla-javaplugin.so: symbolic link to `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so'

ryan@ryan-laptop:~/Projects$ ls /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7
libjavaplugin_oji.so

ryan@ryan-laptop:~/Projects$ file /opt/firefox/plugins/libjavaplugin_oji.so
/opt/firefox/plugins/libjavaplugin_oji.so: symbolic link to `/usr/lib/firefox/plugins/libjavaplugin_oji.so'

---

### Post by bruenig on 2007-01-03
Everything appears to be in place. The only thing I can think of is to remove libjavaplugin_oji.so from the /opt/firefox/plugins directory as it shouldn't be in there since you already have libjavaplugin.so which is symlinking to it. Maybe it being in there twice confuses firefox.

---

### Post by Cirdan7 on 2007-01-03
That did it! Thanks

---

