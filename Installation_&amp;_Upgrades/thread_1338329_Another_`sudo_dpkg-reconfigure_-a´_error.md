---
title: "Another `sudo dpkg-reconfigure -a´ error"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by hbbb on 2009-11-26
Hi,
I recently upgraded an UNR variant dist from jaunty to karmik.

By running `sudo dpkg-reconfigure -a´, noting happens except following error return:

```

$ sudo dpkg-reconfigure -a
[sudo] password for user: 
This is not dpkg install-info anymore, but GNU install-info
See the man page for ginstall-info for command line arguments
install-info: No dir file specified; try --help for more information.
$

```

May someone help in resolving this issue or refine diag?
Many thanks in advance for tips.

best regards.

---

### Post by Sealbhach on 2009-11-26
Why is it that you need to run "sudo dpkg-reconfigure -a".

Is there a problem with updates?

.

---

### Post by hbbb on 2009-11-26
On an AspireOne oao150, in order

1. I updated jaunty and rebooted before upgrading to karmik.
2. Karmik Upgrade was apparently successfull. No broken deps. I cleaned up.
3. Found some problem by using the system: acpi errors in logs; session lock not working anymore after system wakup; terminal and other gnome apps freezing some time...
4. After last karmik kernel update, i removed tuxonice and dependents.

A bit stuck now, would like to rerun `dpkg-reconfigure -a --default-priority'...

---

