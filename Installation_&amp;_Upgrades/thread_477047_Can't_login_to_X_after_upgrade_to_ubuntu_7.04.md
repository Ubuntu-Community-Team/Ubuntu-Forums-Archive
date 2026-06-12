---
title: "Can't login to X after upgrade to ubuntu 7.04"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by jutirain on 2007-06-17
i've upgraded my ubuntu from 6.10 to 7.04 last night.
                                                                                
my machine is vaio sz 92, which has nvidia 7400 grahpics card on it.
                                                                                
                                                                                
after the upgrade,
                                                                                
i got the following message and can't login to X,
                                                                                
i have to use normal login
                                                                                
error message:
===================================
                                                                                
Starting up ...
                                                                                
[  0.310614] PCI: Failed to allocate mem resource #6: 20000@d0000000 for 0000:\
01:00.0
                                                                                
Loading, please wait...
                                                                                
kinit: name_to_dev_t(/dev/disk/by-uuidf65cf65d-3f7b-4905-a67f-81a953cdf35) = s\
da5(8,5)
                                                                                
kinit: trying to resume from /dev/disk/by-uuidf65cf65d-3f7b-4905-a67f-81a953cd\
f35
                                                                                
kinit: No resume image, doing normal login
                                                                                
===================================
                                                                                
so, is there any problem with "resume image"?
                                                                                
                                                                                
i've installed nvidia-glx-new,
                                                                                
when i "sudo startx"
                                                                                
i got only a terminal on the left-top corner, and nothing else...
                                                                                
                                                                                
somebody knows how to solve it?
                                                                                
or there any method to "downgrade" to my original version...

thanks a lot!

---

