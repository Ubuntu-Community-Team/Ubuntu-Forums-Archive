---
title: "Strange behavior of Unison after upgarde tu 18.04"
date: 2018-06-06
forum: Installation &amp; Upgrades
---

### Post by fred66 on 2018-06-06
I have been using Unison to sync my computers for a long time now. Since the Debian repositories don't keep aversion 2.48 (the only one in Ubuntu's repositories) I am relying on static version 2.40.61 to sync with my Debian server. Never had a glitch. After upgrading to 18.04 my Lubuntu laptop, however, starts normally, but at 14% aborts with this mysterious error message:

unison: loadlocale.c:130: _nl_intern_locale_data: Assertion `cnt < (sizeof (_nl_value_type_LC_TIME) / sizeof (_nl_value_type_LC_TIME[0]))' failed.
Aborted (core dumped)

Can anyone help decode this and, hopefully, tell me how to fix this issue? I don't know if it has anything to do with Lubuntu, 18.04, or something else.

Thank you.

---

### Post by lindstream on 2018-07-07
I'm in the exact same situation (long term Unison user, sort of mired in 2.40.61). After updating to 18.04, this error message began to appear (not all the time, but too often for things to work). I've made it work again by setting LC_ALL=C, i.e. I run unison like:

    LC_ALL=C ~/bin/unison-2.40.61-linux-x86_64-text-static

(I also ran sudo locale-gen, but that in itself didn't do it. Perhaps you need to do both, though I'd start with LC_ALL and see if that works.)

Cheers!

---

