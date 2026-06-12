---
title: "Segmentation fault (core dumped) after 16.04 upgrade"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by gmocciaro on 2016-04-26
Hi all,

I'm having this problem after i upgraded my kubuntu from 15.10 to 16.04.
Actually everything works fine, the problem is that whenever i try to use the "sudo" command with a specific user, the "[FONT=monospace][COLOR=#000000]Segmentation fault (core dumped)" message appear.

If i try to cast a command without sudo, everything is fine.
If i try to change user (su username) or login as root (su root) everything is fine.

So, this happens only when i'm logged with the user 'gmocciaro' and i use the sudo command

I even tried to change the /etc/sudoers persmissions to 440 but nothing changed

Can you help me? thanks a lot.
[/COLOR]
[/FONT]

---

### Post by Shura0 on 2016-04-28
I have the same issue. But I cannot login as root because I did not assign password.

---

