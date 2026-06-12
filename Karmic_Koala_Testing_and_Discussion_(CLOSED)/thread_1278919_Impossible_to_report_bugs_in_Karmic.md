---
title: "Impossible to report bugs in Karmic"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by karaluh on 2009-09-30
Since reporting bugs directly in Launchpad is disabled, the only way to report bugs is ubuntu-bug. The problem is: it crashes. The backtrace:

```
Traceback (most recent call last):
  File "/usr/bin/apport-cli", line 403, in <module>
    if not app.run_argv():
  File "/usr/lib/python2.6/dist-packages/apport/ui.py", line 436, in run_argv
    return self.run_report_bug()
  File "/usr/lib/python2.6/dist-packages/apport/ui.py", line 374, in run_report_bug
    response = self.ui_present_report_details()
  File "/usr/bin/apport-cli", line 234, in ui_present_report_details
    response = dialog.run()
  File "/usr/bin/apport-cli", line 82, in run
    response = self.raw_input_char(_('Please choose (%s):') % ('/'.join(self.keys)))
  File "/usr/bin/apport-cli", line 39, in raw_input_char
    sys.stdout.write(text + ' ')
UnicodeEncodeError: 'ascii' codec can't encode character u'\u0119' in position 5: ordinal not in range(128)
```

How can I report this?

---

### Post by overdrank on 2009-09-30
Moved to Karmic Koala Testing and Discussion

---

### Post by LKjell on 2009-09-30
You could try apport-bug and apport-cli first eventually do a reinstall of python-apport and apport packages, or upgrade them first.

---

### Post by karaluh on 2009-10-02
> **LKjell said:**
> You could try apport-bug and apport-cli first

All of them fail with the same error.

> **LKjell said:**
> eventually do a reinstall of python-apport and apport packages, or upgrade them first.

aptitude purge and then install didn't help either.

---

### Post by Amaranth on 2009-10-02
Please file a bug at [https://bugs.launchpad.net/ubuntu/+source/apport/+filebug?no-redirect](https://bugs.launchpad.net/ubuntu/+source/apport/+filebug?no-redirect) then once you get the bug number see if apport-collect will work with it to upload needed info for the bug report.

---

### Post by slakkie on 2009-10-02
> **karaluh said:**
> Since reporting bugs directly in Launchpad is disabled


Come again? I submit 90% of my bugreports without the apport package.

---

### Post by karaluh on 2009-10-02
I think my bug is a dupe of [https://bugs.edge.launchpad.net/ubuntu/+source/apport/+bug/430407](https://bugs.edge.launchpad.net/ubuntu/+source/apport/+bug/430407) I allready apport-collected. If it's not, please let me know so I file new bug.

---

