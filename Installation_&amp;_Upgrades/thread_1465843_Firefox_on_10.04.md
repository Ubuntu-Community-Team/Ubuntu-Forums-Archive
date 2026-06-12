---
title: "Firefox on 10.04"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by sjbaugh on 2010-04-29
I have just upgraded from 9.10 64 bit to 10.04 64 bit.

Mostly smooth but firefox will not run. It started up, said one of my add-ons was not compatible (Silverlight or Moonlight I think) and did not start after that.

When I run it in Terminal I get:

```
steve@steve-desktop:~$ firefox
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/nphelix.so [/usr/lib/mozilla/plugins/nphelix.so: wrong ELF class: ELFCLASS32]
Attempting to load the system libmoon 
Segmentation fault
steve@steve-desktop:~$ 
```


Any Ideas?

Steve

(PS I am using Opera to send this!)

---

### Post by jjcv on 2010-04-30
Looks like the plugin is causing problems.  Go ot

.mozilla/firefox/

you will see a directory name ending in .default.  (Mine is 56l848d5.default).  Change into that and you will see a directory called 'extensions'.

You can either move it by renaming it or deleting it.   

Start firefox and reinstall your extensions.

---

### Post by sjbaugh on 2010-04-30
jjcv,

Thank you for that. I have now got it running but I also had to rename:

/usr/lib/mozilla/extensions/plugins

Only got to sort out Flash plugins and things now!

Thanks for the help,

Steve

---

