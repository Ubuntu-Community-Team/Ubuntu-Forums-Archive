---
title: "preseed late_command won't work"
date: 2017-01-16
forum: Installation &amp; Upgrades
---

### Post by horizn on 2017-01-16
Hi,
I am trying to prepare each installed host for Ansible support, however for some reason it doesn't work for me. In my preseed file I have late_command option:

```

d-i preseed/late_command string \
in-target echo -ne "/target/root/.ssh/ed25519" | ssh-keygen -P '' -o -a 100 -t ed25519 ; \
in-target wget -O /tmp/id_ed25519.pub http://server.domain.com/id_ed25519.pub ; \
in-target cat /tmp/id_ed25519.pub >> /target/root/.ssh/authorized_keys ; \
in-target apt-install bash ; \
in-target chsh -s /bin/bash

```

It is downloading pub key file from server, but for some reason won't place it in proper place (/root/.ssh/authorized_keys). Any ideas why?

---

### Post by horizn on 2017-01-17
The problem is that ssh-keygen or chsh commands are not available during installation process neither in /usr/bin nor in /target/usr/bin.

---

