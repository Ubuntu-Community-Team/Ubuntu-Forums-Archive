---
title: "after 11.04 very slow NAS access and nautilus crashes or hangs"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by vdr60 on 2011-06-27
I have an Iomega StorCenter Pro ix4 mounted in fstab as nfs with this line:
```
10.10.1.104:/nfs/VDRSTORE6 /media/vdrnas6 nfs rw,user,auto 0 0
```

After 11.04 upgrade any access with nautilus freeze or crash it (nautilus). From .xsession-errors I found a lot of "access denied" to all files (even if I do nothing with them) and a lot of row regarding
```
g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
```

my .xsession-errors i like this one (it is a sample from the file I've attacched)

```
(nautilus:1444): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1444): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Error: Couldn't open file '/media/vdrnas6/0007 Libri/C/Lee Child - Destinazione Inferno (Ita Libro).pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/media/vdrnas6/0007 Libri/C/Lee Child - Il Nemico (Ita Libro).pdf': Permission denied.

(nautilus:1444): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1444): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Error loading document: Error opening file: Permission denied

(nautilus:1444): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1444): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1444): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1444): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Error: Couldn't open file '/media/vdrnas6/0007 Libri/C/Lee Child - La Prova Decisiva (Ita Libro).pdf': Permission denied.
Error loading document: Error opening file: Permission denied

(nautilus:1444): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
```

Any idea where or what I can investigate?

---

### Post by vdr60 on 2011-07-02
I investigate more on this issue and found that the problem is strictly nautilus related.

If i open an internal disk it seems that nothing happen, but after some minutes (3-6 min!) a nautilus windows appear!

Title of this post should be changed (but it seems I'm not allowed)

---

### Post by vdr60 on 2011-07-18
The problem still persist with this symptom:
Starting nautilus the first time, also in directories with few files, it seems that nothing happens, but after 3-5 minutes the nautilis windowas appear. 
After it is started all operations in its windows have a good response time.
Any new nautilus windows uses 3-5 minutes to start.


The issue isn't related to the NAS environment.
I tried to change the thread title but i wasn't able...

---

### Post by vdr60 on 2011-07-19
I found a **workaround** to this issue:

After a **sudo killall nautilus** it seems that everytime nautilus start immediatly.

I prefer to close this thread also because title is not so right...

---

