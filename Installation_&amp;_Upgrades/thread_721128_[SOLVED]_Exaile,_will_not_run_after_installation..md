---
title: "[SOLVED] Exaile, will not run after installation."
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by merlyn on 2008-03-11
Hi all, 

for some reason or other Exaile will not run after installation.

I've used the Gutsy debs as provided by the Exaile download page.

There are no dependency issues, and the install went smoothly.

This is what appears when attempting to launch Exaile from a terminal.

```
failed 1
Traceback (most recent call last):
  File "/usr/lib/exaile/exaile.py", line 91, in <module>
    from xl.gui import main as exailemain
  File "/usr/lib/exaile/xl/gui/main.py", line 23, in <module>
    from xl import library, media, audioscrobbler, equalizer, burn, common
  File "/usr/lib/exaile/xl/library.py", line 20, in <module>
    from xl import common, media, db, audioscrobbler, xlmisc, dbusinterface
  File "/usr/lib/exaile/xl/media/__init__.py", line 1, in <module>
    from xl.media import mp3, ogg, flac, wav, wv, mpc, tta
  File "/usr/lib/exaile/xl/media/mp3.py", line 2, in <module>
    from xl import xlmisc
  File "/usr/lib/exaile/xl/xlmisc.py", line 32, in <module>
    from xl import mozembed
  File "/usr/lib/exaile/xl/mozembed.py", line 29, in <module>
    import gtkmozembed
SystemError: dynamic module not initialized properly
```Any suggestions?

**Edit:** Problem resolved, I ended up posting my query in the Exaile support forums.

Why did I not do this from the outset you ask?

Simply because there is much less activity on the Exaile forums, and it seemed that I was more likely to get a useful response here.

However, it turns out that having python-gnome2-extras installed was the source of the grief, though I'm not entirely sure why.

Cheers.

---

