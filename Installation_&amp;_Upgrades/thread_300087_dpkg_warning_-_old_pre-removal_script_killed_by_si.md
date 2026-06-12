---
title: "dpkg: warning - old pre-removal script killed by signal (Interrupt)"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by jude999 on 2006-11-15
What does this mean:
```
dpkg: warning - old pre-removal script killed by signal (Interrupt)

```


I get this when trying to install the last update from drapper to edgy, uim-common. The wole output is this:

```
simon@simon:~$ sudo dpkg --install --force-all /var/cache/apt/archives/uim-common_1%3a1.2.1-3ubuntu2-1nlp1~0edgy1_all.deb 
(Reading database ... 112015 files and directories currently installed.)
Preparing to replace uim-common 1:1.0.0-1ubuntu1 (using .../uim-common_1%3a1.2.1-3ubuntu2-1nlp1~0edgy1_all.deb) ...
ERROR: unbound variable (errobj is-set-ugid?)

*backtrace*
>>(is-set-ugid?)
>>(if (is-set-ugid?) (list (string-append (sys-pkglibdir) "/plugin")) (filter string? (append (list (getenv "LIBUIM_PLUGIN_LIB_DIR") (string-append (getenv "HOME") "/.uim.d/plugin") (string-append (sys-pkglibdir) "/plugin")) (if (getenv "LD_LIBRARY_PATH") (string-split (getenv "LD_LIBRARY_PATH") ":") ()))))
>>(define uim-plugin-lib-load-path (if (is-set-ugid?) (list (string-append (sys-pkglibdir) "/plugin")) (filter string? (append (list (getenv "LIBUIM_PLUGIN_LIB_DIR") (string-append (getenv "HOME") "/.uim.d/plugin") (string-append (sys-pkglibdir) "/plugin")) (if (getenv "LD_LIBRARY_PATH") (string-split (getenv "LD_LIBRARY_PATH") ":") ())))))
>>(require "plugin.scm")
>>(require "init.scm")
>>(*catch (quote errobj) (require "init.scm"))
>>(eq? (quote *init.scm-loaded*) (*catch (quote errobj) (require "init.scm")))

ERROR: unbound variable (errobj custom-reload-customs)

ERROR: unbound variable (errobj custom-choice-rec-sym)

ERROR: unbound variable (errobj plugin-alist)

ERROR: wta to car (errobj t)

dpkg: error processing /var/cache/apt/archives/uim-common_1%3a1.2.1-3ubuntu2-1nlp1~0edgy1_all.deb (--install):
 dpkg: warning - old pre-removal script killed by signal (Interrupt)

Errors were encountered while processing:
 /var/cache/apt/archives/uim-common_1%3a1.2.1-3ubuntu2-1nlp1~0edgy1_all.deb

```

---

