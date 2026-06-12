---
title: "cp command isn't working"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by sohaibma on 2006-11-06
i am installing mozilla firefox 2 on my ubuntu.
when i try to copy the plugins from the firefox 1.5 directory to **Mozilla** firefox 2.0 it shows the following
```
$ sudo cp /usr/lib/firefox/plugins /opt/firefox/plugins
cp: omitting directory `/usr/lib/firefox/plugins'
```

i don't know why it is showing this error, it used to work fine earlier when i used it. i am 100% sure both directories exist. Please keep in mind that cp command works fine when i copy files instead of directories.

please help me

---

### Post by marianom on 2006-11-06
I think that since plugins is a directory you need to add -r to make it copy recursively.

check man cp to confirm, please.

---

### Post by simonn on 2006-11-07
> **marianom said:**
> I think that since plugins is a directory you need to add -r to make it copy recursively.

That will copy /usr/lib/firefox/plugins to /opt/firefox/plugins so you will end up with /opt/firefox/plugins/plugins.

What you need to do is:

```

$ sudo cp /usr/lib/firefox/plugins/* /opt/firefox/plugins

```

---

