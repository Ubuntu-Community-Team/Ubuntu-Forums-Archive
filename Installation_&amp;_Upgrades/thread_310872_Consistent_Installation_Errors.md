---
title: "Consistent Installation Errors"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by le_vainqueur on 2006-12-01
I have tried to install a couple of packages now.  I posted a thread in a different forum about a problem installing GStreamer LAME plugin.  In that case the Sound Juicer will no longer extract CDs.  I just tried to install the Debian menu, and got the same error.  I have listed the error below.

> E: clamav-base: subprocess post-installation script returned error exit status 1

The error was exactly the same each time which suggests to me that there is something fundamentally wrong somewhere in my system.  Any tips?


Thanks

---

### Post by tommcd on 2006-12-02
Are you running clam anti-virus? If so, disable or remove that and see if the problem resolves. You really don't need it unless you are running a network and using it to protect windows machines.

---

### Post by le_vainqueur on 2006-12-02
That worked! Thanks!

---

