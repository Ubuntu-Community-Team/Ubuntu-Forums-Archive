---
title: "Totem and Pidgin broken"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by Dread Knight on 2007-08-26
I'm on gutsy and since a couple of updates, totem, pidgin and the desktop effects are broken.

I'm using another video player now (although i don't like it that much, SMplayer) and meebo.com instead pidgin.

I really wanted to use pidgin... i had pidgin from getdeb... and then when it got replaced with the one from the ubuntu repository, it didn't worked anymore. I tried reinstalling and similar things but no results. (I also can't manage to submit bugs to launchpad, but only when trying to run totem i get an error, both gstreamer and xine versions don't work).

Any suggestions?

---

### Post by kellemes on 2007-08-26
Have your tried running pidgin from the commandline? This may give you some informative output.

---

### Post by Dread Knight on 2007-08-26
hmm, i've wrote pidgin in a terminal and i got this:

(pidgin:9079): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstfaad.so': /usr/lib/gstreamer-0.10/libgstfaad.so: undefined symbol: faacDecDecode
pidgin: symbol lookup error: pidgin: undefined symbol: purple_core_ensure_single_instance


seems to me it's a gstreamer problem :confused:

---

### Post by Dread Knight on 2007-08-28
Also, for totem i get:


(totem:9449): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstfaad.so': /usr/lib/gstreamer-0.10/libgstfaad.so: undefined symbol: faacDecDecode
Segmentation fault (core dumped)




So i think it's a problem with this file (because it's not missing):
 /usr/lib/gstreamer-0.10/libgstfaad.so

:(

---

### Post by mirceade on 2007-08-31
Exact same problems here on Gutsy. This [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/132773](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/132773) seems related. Post a confirmation there as it seems this bug is due to some totem plugin update and reports are starting to emerge.

---

### Post by Dread Knight on 2007-09-01
> **mirceade said:**
> Exact same problems here on Gutsy. This [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/132773](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/132773) seems related. Post a confirmation there as it seems this bug is due to some totem plugin update and reports are starting to emerge.

Thanks! I've posted over there :)

---

### Post by crypticmystic on 2007-10-24
pidgin wise, it appears that the upgrade moved the location of libpurple.* from /usr/local/lib to /usr/lib.    Checking my search path I saw that I had /usr/local/lib ahead of /usr/lib in my LD_LIBRARY_PATH, and uninstall reinstall doesn't fix this.. If you install 7.10 fresh, you only get the lastest copy installed into /usr/lib..  If you upgrade, you may have old versions of libpurple hanging around (like I did)..   So..

> find /usr -name 'libpurple*'
/usr/lib/libpurple-client.so.0.2.1
/usr/lib/libpurple-client.so.0
/usr/lib/libpurple.so.0
/usr/lib/libpurple.so.0.2.1
/usr/local/lib/libpurple.la
l/usr/local/lib/libpurple.so
l/usr/local/lib/libpurple.so.0
/usr/local/lib/libpurple.so.0.0.

I deleted the /usr/local/lib files (the older revision) and it works like a charm!

---

### Post by montgoja on 2007-10-24
Worked like a charm!  thanks!

---

### Post by viherpeukalo on 2007-10-26
Didn't work for me :confused:

---

### Post by kingkookie on 2007-10-26
My error from the command line is "Segmentation Fault."

I just went to Add/Remove Programs... and removed Pidgin and then Re-installed it.  Works perfect.

---

