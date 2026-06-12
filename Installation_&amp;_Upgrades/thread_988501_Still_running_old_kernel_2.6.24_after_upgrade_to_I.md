---
title: "Still running old kernel 2.6.24 after upgrade to Intrepid"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by Aragorn159 on 2008-11-20
I upgraded from Hardy to Intrepid using alt - F2 and then running the command "update-manager -d".
The system is upgraded running gnome 2.24 etc. But it still runs kernel 2.6.24-19.

When I look in the synaptic I can see that kernel 2.6.27 also is installed. 

I already tried running:

```
sudo apt-get dist-upgrade 
```
and
```
 sudo apt-get upgrade
```

Nothing worked, recovery mode also didn't help me.
Can someone help me to solve this problem? How can I upgrade to kernel 2.6.27.

---

### Post by Idefix82 on 2008-11-20
So you don't get the choice at the boot screen? Can you post the output from
```
cat /boot/grub/menu.lst
```

---

