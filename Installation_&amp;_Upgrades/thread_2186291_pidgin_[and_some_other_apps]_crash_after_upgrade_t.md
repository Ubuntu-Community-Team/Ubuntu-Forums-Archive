---
title: "pidgin [and some other apps] crash after upgrade to 13.10"
date: 2013-11-06
forum: Installation &amp; Upgrades
---

### Post by karomann on 2013-11-06
After upgrading to 13.10 some of my apps crash:

-> pidgin fails to start, with error output of pidgin -d:
```

[...]
(23:11:12) Session Management: Using /usr/bin/pidgin.orig as command
(23:11:12) GLib-GObject: value "-1959287660" of type 'gint' is invalid or out of range for property 'weight' of type 'gint'
(23:11:12) prefs: /purple/savedstatus/default changed, scheduling save.
*** Error in `/usr/bin/pidgin.orig': free(): invalid size: 0x00007f998d6c5230 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x80996)[0x7f9987a79996]
/usr/lib/x86_64-linux-gnu/libpango-1.0.so.0(pango_glyph_string_free+0x12)[0x7f9988b7b202]
/usr/lib/x86_64-linux-gnu/libpango-1.0.so.0(+0xe3f6)[0x7f9988b753f6]
/usr/lib/x86_64-linux-gnu/libpango-1.0.so.0(+0xe6f8)[0x7f9988b756f8]
/usr/lib/x86_64-linux-gnu/libpango-1.0.so.0(+0x2130a)[0x7f9988b8830a]
[rest of long long backtrace...]
```

-> google-chrome/chromium crash randomly (segmentation fault), usually while authenticating with http simple authentication. Also, on this browser the text selection on address bar does not work properly - parts of the text are not selected when I try to select it with mouse or keyboard.

Thanks in advance for any help.

---

