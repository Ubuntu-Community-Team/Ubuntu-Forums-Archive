---
title: "software center crash"
date: 2015-01-30
forum: Installation &amp; Upgrades
---

### Post by Andrew F in Australia on 2015-01-30
HI All,

See logs below, both Firefox and Software Centre crash immediately.

I've tried apt-get purge then apt get install software center (no change to the error)

Rather than a reinstall of Ubuntu, can anybody see a fix or where the error's coming from?

Thanks in advance,

Andrew F

Software Centre
```
horace@horace-HP-ProBook-4730s:~$ software-center2015-01-30 17:50:38,386 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2015-01-30 17:50:38,949 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2015-01-30 17:50:38,952 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2015-01-30 17:50:39,005 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2015-01-30 17:50:39,492 - softwarecenter.backend.reviews - WARNING - error creating bsddb: '(22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')' (corrupted?)
2015-01-30 17:50:39,492 - softwarecenter.backend.reviews - ERROR - trying to repair DB failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 358, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 377, in _dump_bsddbm_for_unity
    0600)
DBInvalidArgError: (22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 68 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
Bus error (core dumped)
horace@horace-HP-ProBook-4730s:~$
```

Firefox
```
horace@horace-HP-ProBook-4730s:~$ firefox

(process:5869): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
Bus error (core dumped)
horace@horace-HP-ProBook-4730s:~$ 
(process:5914): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed



```

---

### Post by veddox on 2015-01-30
Can't see any immediate cause from the error logs; but just as a general question: did you change anything recently? If two unrelated programs start crashing simultaneously, there's usually a system fault to blame... Reinstalling the individual programs wouldn't help here. (Note that both programs terminate with a [bus error]("https://en.wikipedia.org/wiki/Bus_error") - I get the impression that the C library has a problem.)

Are you up to date with your updates? Were you playing around with you system in any way? (Once I had the Software Center and the Updater die on me simultaneously because I had changed the link /usr/bin/python to point to python3 instead of python2...)

---

### Post by Andrew F in Australia on 2015-01-30
Hi veddox, 

Thanks for the reply. 

No,  I hadn't readjusted libraries recently.  Maybe a year ago but not since.

Running 14.04, with all updates current. 

Anything obvious caused the crash., now Thunderbird is also acting up. 
F

---

### Post by veddox on 2015-01-31
Found a [similar post]("http://askubuntu.com/questions/445307/firefox-crash-bus-error-core-dumped") on AskUbuntu from a year ago - perhaps there is something there that can help you.

This does seem to be a tricky case, though. Theoretically, a bus error could signal a hardware fault. Have you browsed your system/kernel logs, if there are any related error messages there?

Beyond that, I'm afraid there's nothing I can think of - sorry!

---

