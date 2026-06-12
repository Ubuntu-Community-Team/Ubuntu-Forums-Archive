---
title: "Reinstall problem - &quot;double&quot; system using SSH"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by G_u_s on 2010-10-12
Hi all,

I have updated my desktop computer from 10.04 to 10.10 yesterday using do-release-upgrade. It worked fine (apart from the screen flicker problem I have, see [this thread]("http://ubuntuforums.org/showthread.php?t=1593437")). Except that now, when I connect to this computer using SSH, I get the following message:
```

Linux XXXX-desktop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

765 packages can be updated.
0 updates are security updates.

*** System restart required ***
Last login: Tue Oct 12 16:42:44 2010 from XXXX
XXXX@XXXX-desktop:~$

```

I went to check /etc/motd, and it contains this message. However, I don't understand why it stays like that and is not reset to something correct. I'm afraid maybe something worse happened on the system.

I did the upgrade using an SSH connection coupled to "screen". Maybe it's the cause?

Thank you for your help.

---

### Post by aksoutherland on 2010-10-12
I had the same issue. I also did my upgrade using ssh and screen.
I was able to clear it up by removing the contents of /etc/motd.tail and /etc/motd.
Once these 2 files were cleared, everything went back to normal.

Hope this helps.

---

### Post by G_u_s on 2010-10-12
Thanks a lot, it worked indeed.

Still, I'd like to know what caused this, if it was something more important than just a text file, etc.

---

### Post by Geryon on 2010-10-12
I had the exact same problem as well.  I think it's probably a left over from 10.04 that the upgrade didn't look for.

---

### Post by aksoutherland on 2010-10-12
I agree, I think it is just something that the upgrade process missed when cleaning up.

---

### Post by G_u_s on 2010-10-14
Ok, thank you guys =)

---

