---
title: "Error at start up"
date: 2015-02-25
forum: Installation &amp; Upgrades
---

### Post by poetical on 2015-02-25
I have had 14.04 as an upgrade for a while now, and am running a Toshiba satellite L-500 with an intel pentium duel core. Ever since I upgraded I have been receiving this message at start up and it persists when upgrading and updating software, I have tried to fix it but my technical abilities as a programmer are limited, is it possible to get some help.

the Error message is: libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 44: ignoring bad line starting with 'snd-hda-intel'

any assistance would be greatly appreciated, thank you.

---

### Post by ajgreeny on 2015-02-25
Show us the contents of that file mentioned with command ```
cat /etc/modprobe.d/alsa-base.conf | grep snd-hda-intel
```

---

### Post by MYaseen208 on 2015-09-08
I have the same problem and the contents of 

cat /etc/modprobe.d/alsa-base.conf | grep snd-hda-intel

are 

snd-hda-intel model=generic


Any help to solve this problem will be highly appreciated. Thanks

---

