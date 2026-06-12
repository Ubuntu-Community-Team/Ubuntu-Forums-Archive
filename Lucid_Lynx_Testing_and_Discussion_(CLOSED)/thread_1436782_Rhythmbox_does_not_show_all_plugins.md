---
title: "Rhythmbox does not show all plugins"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Killigrew on 2010-03-23
Hi

I have a problem with rhythmbox.
It does not show all installed plugins in the plugins submenü.
for example the new ubuntu store isn't shown (package is installed)
I did already reinstall it but it didn't help.
if i start rhythmbox in the terminal i get following output multiple times:
```

(rhythmbox-metadata:7977): GLib-CRITICAL **: g_date_new_dmy: assertion `g_date_valid_dmy (day, m, y)' failed

(rhythmbox-metadata:7977): GLib-CRITICAL **: g_date_valid: assertion `d != NULL' failed

(rhythmbox-metadata:7977): GStreamer-CRITICAL **: gst_value_set_date: assertion `g_date_valid (date)' failed

(rhythmbox-metadata:7977): GLib-CRITICAL **: g_date_free: assertion `d != NULL' failed

```does somebody have a similar problem or know how to fix it?

greetings from germany
killigrew

---

### Post by Killigrew on 2010-03-23
ok, i found something out,
i compared my installation with the lucid Beta1 Live CD.
The difference i found is that i have two files
rhythmbox
rhythmbox-client
in /usr/local/bin and in /usr/bin
on the liveCD they are only in /usr/bin
if i rename the files in /usr/local/bin
rhythmbox doesn't start any more, just gives following error message:
rhythmbox: symbol lookup error: rhythmbox: undefined symbol: _PyGObject_API

i found out that rhythmbox in /usr/local/bin is an old version while /usr/bin ist the actual version
so the main task is zu fix the _PyGObject_API error.

please, does somebody know how to fix this?
greetings

---

