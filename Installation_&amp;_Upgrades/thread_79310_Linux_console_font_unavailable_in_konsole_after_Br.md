---
title: "Linux console font unavailable in konsole after Breezy upgrade"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by pestie on 2005-10-20
Hi! I upgraded my laptop to Breezy and now the Linux console font is unavailable in Konsole. I get this error:

```
Font
'misc-console-medium-r-normal--16-160-72-72-c-80-iso10646-1'
not found.

Check /usr/share/doc/konsole/README.Linux-font for help.
```

Well, I did that (which is what I originally did to get the font in Hoary) and it doesn't help. The xconsole-fonts package is installed, I ran dpkg-reconfigure as instructed, and still no love. Anyone have a fix for this one? Thanks.

---

### Post by bertilow on 2005-10-20
[QUOTE=pestie]Hi! I upgraded my laptop to Breezy and now the Linux console font is unavailable in Konsole. I get this error:

```
Font
'misc-console-medium-r-normal--16-160-72-72-c-80-iso10646-1'
not found.

Check /usr/share/doc/konsole/README.Linux-font for help.
```

Well, I did that (which is what I originally did to get the font in Hoary) and it doesn't help. The xconsole-fonts package is installed, I ran dpkg-reconfigure as instructed, and still no love. Anyone have a fix for this one? Thanks.[/QUOTE]

The easiest fix is to avoid the problem: use another font. Choose one with the "Custom" option just below the "Unicode" option.

I use "Courier New" (available in the "msttcorefonts" package), but other fixed width fonts will probably do just as well, unless there are some special characters in "misc-console" that you need and that are not available in other fonts.

(As long as you use a Unicode - UTF-8 - locale, of course...)

---

### Post by pestie on 2005-10-21
Well, maybe I'm lame, but I really like having a konsole that's a near-clone of the Linux text console. I can switch everything to be Xterm-like by default and I have no problems. But I find the Linux console font very easy on my eyes.

---

### Post by pestie on 2005-10-24
Nobody's got a fix for this? If not, this is the last time I'll bump this thread.

---

