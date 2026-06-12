---
title: "Language (locales) crashed after update."
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by sadnem on 2010-07-27
So after doing an update that included some language files (i don't remember which ones exactly) something crashed and now i get this type of errors in terminal:
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "C",
    LC_ALL = "es_ES.UTF-8",
    LANG = "es_ES.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory

```And if i start a teminal the first line is:
```
bash: warning: setlocale: LC_ALL: cannot change locale (es_ES.UTF-8)

```I've read a bunch of similar topics regarding this and tried everything (creating symlinkx, changing /etc/environment, forcing the change of LANG and LC_ALL in .bashrc, etc... and it's a very problematic error because I can't manage almost nothing in Spanish now (For example i can't play a video with spanish subtitles because it will make mplayer crash)

---

