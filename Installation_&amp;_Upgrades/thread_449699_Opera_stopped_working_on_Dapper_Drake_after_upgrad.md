---
title: "Opera stopped working on Dapper Drake after upgrade"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by Ba|der on 2007-05-20
I've applied latest security updates on Dapper and the webrowser Opera that is installed and updated via the universe repository will not start any more. Running on command line gives this output:
```

balder@ibuddie:~$ opera &

[1] 15105
Balder@ibuddie:~$ X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
 
```

Any ideas?

---

### Post by boredandblogging.com on 2007-05-21
Maybe it has something to do with this? [http://my.opera.com/desktopteam/blog/2007/04/06/hotfix](http://my.opera.com/desktopteam/blog/2007/04/06/hotfix)

Try grabbing the latest version of opera and seeing if you still have problems.

---

### Post by Ba|der on 2007-05-22
> **boredandblogging.com said:**
> Maybe it has something to do with this? [http://my.opera.com/desktopteam/blog/2007/04/06/hotfix](http://my.opera.com/desktopteam/blog/2007/04/06/hotfix)

Try grabbing the latest version of opera and seeing if you still have problems.

Thanks. I downloaded one of the .deb packages from the above link. Uninstalled Opera and installed the package=Go. (So I did not try to edit xorg.conf as mentioned). 

First I'd thought got a advertisementpage as homepage in Opera, but seems it's a new feature in Opera called "Speed dial".

:popcorn:

---

