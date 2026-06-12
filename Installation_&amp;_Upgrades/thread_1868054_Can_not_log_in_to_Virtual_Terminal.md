---
title: "Can not log in to Virtual Terminal?"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by dirtrider1 on 2011-10-23
I'm having trouble logging in to my virtual terminals. I'm running Ubuntu 11.10 64bit on my laptop. After entering my username and password it says "module is unknown" and brings me back to the username prompt. In auth.log I see this -

```
Oct 23 14:24:28 NWMDV6 login[2874]: PAM adding faulty module: /lib/security/pam_access.so
Oct 23 14:24:28 NWMDV6 login[2874]: pam_securetty(login:auth): access denied: tty '/dev/tty1' is not secure !
Oct 23 14:24:30 NWMDV6 login[2874]: pam_unix(login:auth): check pass; user unknown
Oct 23 14:24:30 NWMDV6 login[2874]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty1 ruser= rhost=
Oct 23 14:24:33 NWMDV6 login[2874]: FAILED LOGIN (1) on '/dev/tty1' FOR 'UNKNOWN', User not known to the underlying authentication module
Oct 23 14:24:42 NWMDV6 login[2874]: Module is unknown
Oct 23 14:25:26 NWMDV6 sudo:  nikolas : TTY=pts/0 ; PWD=/var/log ; USER=root ; COMMAND=/usr/bin/vim auth.log

```

---

### Post by conradin on 2011-10-23
Folks in a fedora forum (Hush -- balasphemy! -- I know)
suggest restarting crond
to solve a similar problem
Then there is discussion of a bug in LIB_pam

---

### Post by dirtrider1 on 2011-10-24
> **conradin said:**
> Folks in a fedora forum (Hush -- balasphemy! -- I know)
suggest restarting crond
to solve a similar problem
Then there is discussion of a bug in LIB_pam

Yeah I tried restarting the cron service if that's what you mean but I'm still experiencing the issue. Could you provide me a link by any chance to any more information on the bug the Fedora people are talking about? Thanks

---

