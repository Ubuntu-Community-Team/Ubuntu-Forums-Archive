---
title: "SSH PermitRootLogin issue in Gutsy"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by fluentbit on 2007-11-01
I recently did a fresh install of 7.10 Gutsy. I have a need to rsync (via ssh) to this new box as root to backup files. I followed the following tutorial.

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

This worked on Feisty, but on my new install of Gutsy, I keep getting this error:

Nov  1 22:31:54 arioch sshd[20724]: User root not allowed because account is locked
Nov  1 22:31:54 arioch sshd[20725]: input_userauth_request: invalid user root

By default, and this is not news to me, the root account is locked.

$ passwd -S root
root L 11/02/2007 0 99999 7 -1

However, I have this exact same setup on all other boxes and it works fine. Unlocking the account resolves the problem, but I don't want to have to unlock it if it's not necessary.

Does anyone know what would be causing this strangeness?

---

### Post by dabang on 2007-11-02
If I get it right, you want to keep the root account of the box you want to make a ssh connection to locked? I don't think this is possible. You need to give root a password if you want to ssh as root. Maybe somebody could correct me if I'm wrong...?
But is it really necessary to connect as root? I think default sshd_config doesn't allow root login. At least, if this box is somewhere on the internet I wouldn't allow root logins.

---

### Post by lolindrath on 2007-11-02
Hello,

It is possible but not advisable security-wise. You can login as a regular user and then do an su to get a root shell.

Here's how to allow Root login:

In /etc/ssh/sshd_config

change:
```
PermitRootLogin no
```

to:
```
PermitRootLogin yes
```

---

### Post by fluentbit on 2007-11-04
Sorry, I should have provided a few more details. I agree in that permitting root access via SSH could have security concerns. In this case, the PermitRootLogin is using 'forced-commands-only' to allow root to login and do a specific command to backup (via rsync) the system.

Although in theory it does make sense that if the account is locked, the root user should not be able to login via ssh regardless of the ssh configuration, it works on 3 other systems with the root account locked, but not on this one.

I'm still stumped.

---

### Post by leutzdave on 2007-11-04
> **fluentbit said:**
> Sorry, I should have provided a few more details. I agree in that permitting root access via SSH could have security concerns. In this case, the PermitRootLogin is using 'forced-commands-only' to allow root to login and do a specific command to backup (via rsync) the system.

Although in theory it does make sense that if the account is locked, the root user should not be able to login via ssh regardless of the ssh configuration, it works on 3 other systems with the root account locked, but not on this one.

I'm still stumped.



This is happening with me too, on Gutsy, no where can I find the PermitRootLogin option by doing:
          grep -iR PermitRootLogin /etc/*

and there is no /etc/ssh/sshd_config

So should I make one and add the PermitRootLogin=yes   ??? (notes boxen are behind a firewall)

---

