---
title: "Preseed ignored on 1604"
date: 2016-06-03
forum: Installation &amp; Upgrades
---

### Post by J&#7885;hn on 2016-06-03
Hi All

I have a preseed setup which works fine with Ub12 and Ub14 (and the variants inbetween), but when I try to launch it from Ub16 I am returned to the initial boot menu.

Has anything changed in this regard with Ub16 which would prevent it from working? I can find nothing mentioned about it.

Method-

Boot from install iso (tried both mini and server isos)
Press ESC at boot menu
When *boot:* appears, type:   install auto=true url={my preseed file url} hostname={hn}

This works fine on older versions but not on Ubuntu 16.04

Any advice appreciated

J&#7885;hn

---

### Post by J&#7885;hn on 2016-06-03
Ah I got it. I'll post the solution here for anyone else may be interested.

At boot, append these:

```
auto=true url={url} hostname={hostname} ---
```

This is in the docs but isn't very clear for those of us used to doing things the previous way, hope it helps someone.

J&#7885;hn

---

