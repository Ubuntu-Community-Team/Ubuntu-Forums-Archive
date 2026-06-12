---
title: "[SOLVED] System Monitor Segfaults on Filesystems Tab"
date: 2008-07-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by BwackNinja on 2008-07-17
Whenever I have a partition mounted other than my main one and go to the filesystem tab of gnome-system-monitor, it segfaults with this error:

```
(gnome-system-monitor:5768): glibmm-WARNING **: Failed to wrap object of type 'GHalMount'. Hint: this error is commonly caused by failing to call a library init() function.
Segmentation fault
```

it sounds like this: [https://bugs.launchpad.net/ubuntu/+source/glibmm2.4/+bug/243992](https://bugs.launchpad.net/ubuntu/+source/glibmm2.4/+bug/243992) but this was apparently resolved.

---

### Post by psyke83 on 2008-07-17
> **BwackNinja said:**
> Whenever I have a partition mounted other than my main one and go to the filesystem tab of gnome-system-monitor, it segfaults with this error:

```
(gnome-system-monitor:5768): glibmm-WARNING **: Failed to wrap object of type 'GHalMount'. Hint: this error is commonly caused by failing to call a library init() function.
Segmentation fault
```

it sounds like this: [https://bugs.launchpad.net/ubuntu/+source/glibmm2.4/+bug/243992](https://bugs.launchpad.net/ubuntu/+source/glibmm2.4/+bug/243992) but this was apparently resolved.

Resolved upstream yes, in Ubuntu no. If you check the bug (that's a duplicate you linked to), it's marked "Fixed Released" for the upstream bug. The package in Ubuntu (glibmm2.4) is only marked "Fix Committed", which indicates that the fix is ready, but not yet released.

---

### Post by BwackNinja on 2008-07-22
Yay! Its fixed in intrepid now!

---

### Post by andrek on 2008-07-22
Is gedit also crashing for you guys?

---

### Post by BwackNinja on 2008-07-22
It was before, I don't remember if it is now. It used to crash just the first time I'd try to use it, but the rest of the times would be fine.

---

### Post by spamzilla on 2008-07-22
> **andrek said:**
> Is gedit also crashing for you guys?

Yep it is for me after installing 32 updates. I can't restart atm to see if a simple restart is needed to fix the problem.

edit

Just restarted, gedit still segments when I try to open it from terminal:

> 
matt@matt:~$ gksudo gedit /etc/modprobe.d/blacklist
(gedit:6024): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(gedit:6024): GLib-CRITICAL **: g_error_free: assertion `error != NULL' failed

(gedit:6024): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(gedit:6024): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.17.4/gio/gfile.c:5438):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)


---

