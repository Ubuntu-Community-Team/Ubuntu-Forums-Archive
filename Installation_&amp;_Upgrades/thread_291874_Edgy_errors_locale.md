---
title: "Edgy errors: locale"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by jchau on 2006-11-03
Since upgrading to Edgy (and while upgrading), I've gotten many errors like the following: 
> /etc/cron.daily/man-db:
mandb: can't set the locale; make sure $LC_* and $LANG are correct
/etc/cron.daily/sysklogd:
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").


Here is the output of the command "locale":
> LANG=en_US.UTF-8
LANGUAGE=en_US:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=


How do I fix this? Are these settings valid? If so, what else can I do? If not, what should they be?

---

### Post by Silent Warrior on 2006-11-03
I got those too, but I don't think it's all that much to worry about. Localization translates right into "text-swapping", I seriously doubt it has anything to do with actual code-interpretation. Of course, if, by some strange mishap, you've been "relocated" to a place with a language you can't possibly understand, then you'd be in trouble. (I got a strange mix of english and swedish (my language), and a broken icon.)
You could try setting your locale-settings manually to use the formatting suggested in the error-messages, quotations and all. (Back up!) I don't know which file to edit, though... Well, if you want, that is. Double-check that you have the localization, and that it's installed properly, just to be sure. Synaptic for president!

---

### Post by lizard_b on 2006-11-04
The locale issues DO seem to be having an effect.  Since the upgrade, much of my DVD related software won't work.

For example, devede says:
```
(devede:8810): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
DeVeDe 2.4
Traceback (most recent call last):
  File "/usr/bin/devede", line 43, in ?
    import devede_convert
  File "/usr/lib/devede/devede_convert.py", line 38, in ?
    locale.setlocale(locale.LC_ALL,"")
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
```


k9copy says:
```
An error occured while Burning DVD :
The pad was 18 for file VIDEO_TS.IFO
mkisofs: Implementation botch. Video pad for file VIDEO_TS.VOB is -18
mkisofs: Either the *.IFO file is bad or you found a mkisofs bug.
Insert an other DVD

An error occured while Burning DVD :
INFO: ISO-8859-1 character encoding detected by locale settings.
Assuming ISO-8859-1 encoded filenames on source filesystem,
use -input-charset to override.
The pad was 18 for file VIDEO_TS.IFO
mkisofs: Implementation botch. Video pad for file VIDEO_TS.VOB is -18
mkisofs: Either the *.IFO file is bad or you found a mkisofs bug.
Insert an other DVD

```

---

### Post by lizard_b on 2006-11-04
As a follow up, I was able to restore devede to function by just commenting out all the broken locale gets/sets.

k9copy is still a mystery to me.

---

### Post by Silent Warrior on 2006-11-05
So I was wrong. Drat! (Interesting localization-hiccup: System-language is set to swedish all around (although I like to keep a bunch of other languages around in case of multi-lingual needs - you never know, maybe I'll want to test myself), and aMule gives me french Yes/No-buttons. :-k It IS set to system-default, but... It doesn't give me any problem, just a side-note. Dapper didn't do this. :p )

Have you tried that -input-charset-option for k9?

---

