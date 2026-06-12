---
title: "Installed Trusty 14.04.1 now 14.04.3 with shorter EOL, what happened?"
date: 2016-01-06
forum: Installation &amp; Upgrades
---

### Post by oceola2 on 2016-01-06
Was this due to a kernel update or some arbitrary change in the os-release file?
Can I edit the os-release file so I can maintain the 14,04.1 LTS lifespan?

---

### Post by deadflowr on 2016-01-06
> **oceola2 said:**
> Was this due to a kernel update or some arbitrary change in the os-release file?
Can I edit the os-release file so I can maintain the 14,04.1 LTS lifespan?

This:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Basically, 14.04.3 is 14.04.
But the hardware stack is based on that for 15.04.
That ends support coming sometime over the summer.
But worry not, as you should be able to move up to the last hardware stack upgrade for 14.04 based on xenial's (16.04)
Which will last for the rest of 14.04's duration.

Beyond all that, though, the rest of 14.04 will be supported until 2019.

---

### Post by oceola2 on 2016-01-06
@deadflowr - Thank you. :)

---

### Post by sudodus on 2016-01-08
Do not let the output of ```
lsb_release -a
``` confuse you :-)

Please post the output of the following command! It will show what kernel you are running. If a kernel in the 3.13 series, it is still Trusty and you have LTS.

```
uname -a
```

The Ubuntu system will not upgrade to a newer kernel series via normal updates/upgrades, you have to upgrade the hardware enablement stack manually. Did you do that?

[LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

