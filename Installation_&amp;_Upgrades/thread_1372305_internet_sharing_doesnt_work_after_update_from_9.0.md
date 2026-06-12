---
title: "internet sharing doesnt work after update from 9.04 to 9.10"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by lulaz on 2010-01-04
Hello,

Subject tells everything. After upgrading Jaunty to Karmic internet sharing (iptables) stoped working. Nothing in iptables configuration was changed. 
```

# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```Computers behind my ubuntu router can ping it, have access to it (apache, samba, etc.). Only internet isnt forwarding. Clients configuration is the same as before upgrade. 

Please help, thats very important and need to be fixed asap.

Rgards, 
lulaz

---

### Post by lulaz on 2010-01-04
I forgot to write that ubuntu router has internet access - no problems with that. Only connection sharing.

---

### Post by lulaz on 2010-01-04
solved @ [http://ubuntuforums.org/showthread.php?t=1372353](http://ubuntuforums.org/showthread.php?t=1372353)

---

