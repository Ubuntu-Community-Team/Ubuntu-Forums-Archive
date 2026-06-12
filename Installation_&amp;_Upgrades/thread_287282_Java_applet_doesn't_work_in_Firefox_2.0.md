---
title: "Java applet doesn't work in Firefox 2.0"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by DC@DR on 2006-10-28
Hi,

I'm using Dapper and I manually installed the Firefox 2.0 few days ago when it was officially released. I put it to /opt/firefox/, and followed this instruction: [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion), and it works pretty nice for me. But today I found a problem that whenever I try to open a java applet webpage, FF crashes right away. Here is what I have:
```

xxxxxxx@ubuntu:/opt/firefox/plugins$ ls -lah
total 28K
drwxr-xr-x  2 root root 4.0K 2006-10-25 07:28 .
drwxr-xr-x 12 root root 4.0K 2006-10-11 09:58 ..
lrwxrwxrwx  1 root root   48 2006-10-25 07:28 flashplayer.xpt -> /usr/lib/mozilla-firefox/plugins/flashplayer.xpt
lrwxrwxrwx  1 root root   50 2006-10-25 07:28 libflashplayer.so -> /usr/lib/mozilla-firefox/plugins/libflashplayer.so
lrwxrwxrwx  1 root root   49 2006-10-25 07:28 libjavaplugin.so -> /usr/lib/mozilla-firefox/plugins/libjavaplugin.so
-rwxr-xr-x  1 root root  19K 2006-10-11 09:57 libnullplugin.so
lrwxrwxrwx  1 root root   54 2006-10-25 07:28 libunixprintplugin.so -> /usr/lib/mozilla-firefox/plugins/libunixprintplugin.so
lrwxrwxrwx  1 root root   54 2006-10-25 07:28 mplayerplug-in-gmp.so -> /usr/lib/mozilla-firefox/plugins/mplayerplug-in-gmp.so
lrwxrwxrwx  1 root root   55 2006-10-25 07:28 mplayerplug-in-gmp.xpt -> /usr/lib/mozilla-firefox/plugins/mplayerplug-in-gmp.xpt
lrwxrwxrwx  1 root root   53 2006-10-25 07:28 mplayerplug-in-qt.so -> /usr/lib/mozilla-firefox/plugins/mplayerplug-in-qt.so
lrwxrwxrwx  1 root root   54 2006-10-25 07:28 mplayerplug-in-qt.xpt -> /usr/lib/mozilla-firefox/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx  1 root root   53 2006-10-25 07:28 mplayerplug-in-rm.so -> /usr/lib/mozilla-firefox/plugins/mplayerplug-in-rm.so
lrwxrwxrwx  1 root root   54 2006-10-25 07:28 mplayerplug-in-rm.xpt -> /usr/lib/mozilla-firefox/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx  1 root root   50 2006-10-25 07:28 mplayerplug-in.so -> /usr/lib/mozilla-firefox/plugins/mplayerplug-in.so
lrwxrwxrwx  1 root root   54 2006-10-25 07:28 mplayerplug-in-wmp.so -> /usr/lib/mozilla-firefox/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx  1 root root   55 2006-10-25 07:28 mplayerplug-in-wmp.xpt -> /usr/lib/mozilla-firefox/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx  1 root root   51 2006-10-25 07:28 mplayerplug-in.xpt -> /usr/lib/mozilla-firefox/plugins/mplayerplug-in.xpt
lrwxrwxrwx  1 root root   43 2006-10-25 07:28 nphelix.so -> /usr/lib/mozilla-firefox/plugins/nphelix.so
lrwxrwxrwx  1 root root   44 2006-10-25 07:28 nphelix.xpt -> /usr/lib/mozilla-firefox/plugins/nphelix.xpt

```
I think I do have libjavaplugin.so which should help to deal with java applet stuffs, but why my FF crashes like that? Please tell me what's wrong here, thanks :)

EDIT: The output in terminal when firefox crashes is:
/opt/firefox/run-mozilla.sh: line 131:  7128 Segmentation fault      "$prog" ${1+"$@"}

---

### Post by cian42 on 2006-10-28
same problem here...can't use meebo, bloglines etc. cause firefox(2.0, 1.5, flock)keeps crashing.

---

### Post by DC@DR on 2006-10-28
OK, I got my problem fixed, I removed 2 plugins: Mr Tech Local and Cute Menu, and then it works fine again, kinda weird, huh. But it's really a pain since I love those above plugins, darn :(

---

### Post by cian42 on 2006-10-28
workaround for flash and java from de ubuntu guide

Note: if firefox crashes when visiting a website with flash content, do the following: 
sudo gedit /usr/bin/firefox

and add the following line as last but one line of the file: 
export XLIB_SKIP_ARGB_VISUALS=1

it worked for me.

---

