---
title: "locales - screen_font"
date: 2006-04-12
forum: Installation &amp; Upgrades
---

### Post by zigi on 2006-04-12
I want to use czech language (iso-8859-2) and some special chars are not right displayed before I type dpkg_reconfigure console-tools. Then it seems good, all chars are displayed right.

My settings:
/etc/environment
```

LANG=cs_CZ
LANGUAGE="en_CZ:en_US:en_GB:en"
LC_MESSAGES=C

```

/etc/console-tools/config
```

SCREEN_FONT=lat2-sun16
SCREEN_FONT_vc*=lat2-sun16     * = 2..6

APP_CHARSET_MAP=iso02
APP_CHARSET_MAP_vc*=iso02     * = 2..6

```

and cs_CZ locales are generated..

PS: I use Dapper Drake 6.06

---

