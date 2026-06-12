---
title: "Problem with locale"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by moh_lo on 2007-07-08
Hello all

I just install ubuntu from my debian with a how to find on the net.  [https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/linux-upgrade.html]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/linux-upgrade.html")

But like stupid man I set my /etc/environment like that
```
root@postTv:/home/tv# more /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANGUAGE=fr
LC_ALL=fr_FR@euro
LANG=fr_FR@euro

```

(Yes I'm french)
And now when I install a paquet with apt I have some bad looking messages like that
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "fr",
        LC_ALL = "fr_FR@euro",
        LANG = "fr_FR@euro"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```
But the installation works without problem.

Whatever.
I want use freevo but freevo is more difficult with locale than apt and it doesn't work.
```
root@postTv:/home/tv# freevo
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/freevo/main.py", line 57, in <module>
    import config
  File "/usr/lib/python2.5/site-packages/freevo/config.py", line 52, in <module>
    locale.setlocale(locale.LC_TIME,'')
  File "/usr/lib/python2.5/locale.py", line 476, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

```

I don't have to have a french system, and I would like have a /etc/environment like us-people.

If anyone can send me one?

Thanks

---

### Post by Rui Pais on 2007-07-08
Hi,
you need to set your locales first. Here a link to general info on locale-gen:
[https://help.ubuntu.com/community/LocaleConf](https://help.ubuntu.com/community/LocaleConf)

---

### Post by moh_lo on 2007-07-09
Hi

I read your link and do some stuffs describe on it.

I don't know exactly how and I don't know exactly why but it's work.

Thanks a lot

---

### Post by Rui Pais on 2007-07-09
> **moh_lo said:**
> Hi

I read your link and do some stuffs describe on it.

I don't know exactly how and I don't know exactly why but it's work.

Thanks a lot

No prob :)

The issue was simply that you don't have, when edit /etc/environment, locales for French.
You just need to configure your system to that 'locale' on locales list (dpkg-reconfigure) and generate it with locale-gen. Easy but not exactly obvious. 
:)

Have fun.

---

