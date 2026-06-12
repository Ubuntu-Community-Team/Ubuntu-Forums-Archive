---
title: "How to disable a daemon?"
date: 2015-07-29
forum: Installation &amp; Upgrades
---

### Post by siggi2 on 2015-07-29
Lubuntu 14.04.2 

Hi,

I am not a professional exorcist ;) but would like to disable the command ```
syndaemon -d -t
``` that I had invoked. I.e., I would like to have the default state for my notebook touchpad. How can I do this?

Thank you,

siggi

---

### Post by ian-weisser on 2015-07-30
'sudo pkill syndaemon' is one way.

---

### Post by SeijiSensei on 2015-07-30
Ian's method will kill the current instance, but the daemon will probably start itself again upon reboot.  If you mean you logged in and typed that command in a session, then Ian's method will do the trick.

If you set it up to load at boot, you need to tell us how.  There are many ways to start a daemon at boot.  How did you do it?

---

