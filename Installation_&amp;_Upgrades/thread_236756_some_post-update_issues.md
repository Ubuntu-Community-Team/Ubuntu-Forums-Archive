---
title: "some post-update issues"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by Blues- on 2006-08-15
Just upgraded to Dapper last night,
The installer failed just after the last package had been installed and configured with something that my system could be unstable. 
I rebooted into my new Dapper installation without major problems.  But the cleaup process of the installation did not execute so now i seem to have new partitions on my system that I'm not sure if they are supposed to be there or what ? ..
```

/var/run tmpfs varrun  0% (1%) 758.72 MB 220.00 KB 758.94 MB 
/var/lock tmpfs varlock  0% (1%) 758.93 MB 4.00 KB 758.94 MB 
/dev tmpfs udev  0% (1%) 758.79 MB 152.00 KB 758.94 MB 
/dev/shm tmpfs devshm  0% (1%) 758.94 MB 0.00 KB 758.94 MB 

```

Can anyone tell me if this is normal and/or how do i manually exeute the cleanup process that the installer should have run.

ps. MRTG is also broken .. with the message
```
ERROR: Creating templock /var/lock/mrtg/_etc_mrtg_.xxxxx.com.cfg_l_6305: No such file or directory at /usr/bin/mrtg line 1645.

```

Don't know if the mrtg problem is related to the "never executed" cleanup process.

Thanks in advance,
Cheers,
Konni.

---

