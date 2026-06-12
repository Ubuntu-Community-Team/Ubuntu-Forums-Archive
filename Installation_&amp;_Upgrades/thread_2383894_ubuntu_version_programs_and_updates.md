---
title: "ubuntu version programs and updates"
date: 2018-01-30
forum: Installation &amp; Upgrades
---

### Post by espectro2 on 2018-01-30
I  would like to know why the iso I downloaded from ubuntu was 16.04.2 but  at the moment it is running version 16.04.1 at least is this printing  running command uname -a do I have this is normal to change version?
It is configured for long support updates because it was 16.04.2 to 16.04.1
4.13.0-32-generic #35~16.04.1-Ubuntu

it  is possible to update the repositories change if update download server  via terminal without entering programs and updates via graphical  interface
Thanks for listening.

---

### Post by cruzer001 on 2018-01-30
Do you mean

```
lsb_release -a
```

---

### Post by Impavidus on 2018-01-31
That final version number refers to the version of the live disk image. 16.04 is the original, 16.04.1 has some updates already included, 16.04.2 has some more updates included and the HWE stack, 16.04.3 adds some more opdates and so 16.04.4 and .5. After you installed the system and installed all available updates, that number doesn't really matter. The only difference is that 16.04 and 16.04.1 don't install the HWE stack. If everything works fine, that doesn't matter. Else, you can add it yourself.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by espectro2 on 2018-02-01
I actually got confused as kernel might be 16.04.1 and the ubuntu version I'm running is 16.04.3
Thanks for listening.
 lsb_release -a Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

uname -a 4.13.0-32-generic #35~16.04.1-Ubuntu

---

### Post by cruzer001 on 2018-02-01
Your fully updated so its all good :)

---

### Post by espectro2 on 2018-02-01
thanks for listening

---

