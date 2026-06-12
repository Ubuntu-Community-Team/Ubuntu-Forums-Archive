---
title: "X server failed to start after 60 seconds"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by AdamTheNewbie on 2008-01-05
Hi,

  On my Dell 530 with Dell installed Feisty (7.04)  update manager took me to 7.10.  The gnome desktop works (ctrl-alt-f7). Actually, everything appears to work... 

Except: tty1 (ctrl-alt-f1) keeps displaying messages (about every minute). Message is below. 
    
Any help is appreciated!
Regards,
Adam.


```
Ubuntu 7.10 ubuntu tty1

ubuntu login: Traceback (most recent call last):
                       File "/usr/sbin/oem-config-dm", line 136, in <module>
                         sys.exit(dm.run(*sys.argv[3:]))
                           File "/usr/sbin/oem-config-dm", line 66, in run
                      raise XStartupError, "X server failed to start after 60 seconds"
         __main__.XStartupError: X server failed to start after 60 seconds
Ubuntu 7.10 ubuntu tty1
```

---

