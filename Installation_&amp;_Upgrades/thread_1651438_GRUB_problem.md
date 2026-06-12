---
title: "GRUB problem"
date: 2010-12-23
forum: Installation &amp; Upgrades
---

### Post by pedi0022003 on 2010-12-23
I have recently installed Ubuntu 10.10 and it's working fine.The only problem I have is that grub is not showing and I automatically come across the login screen.Please note that I only have Ubuntu on my computer.  
Any help would be appreciated!

---

### Post by garvinrick4 on 2010-12-23
No grub menu when only one install defaults to boot that Operating system.
to see grub menu in terminal
```
grep menuentry /boot/grub/grub.cfg
``````
gedit /boot/grub/grub.cfg
```Above shows your whole config file if you want to look at it.

## You made 2 threads the same in different locations, mod's will be on you like stink
           on a Puppy. Only make one thread they show up.

---

### Post by Quackers on 2010-12-23
If you particularly want to see the grub menu you should hold down the shift key while booting.

---

### Post by sikander3786 on 2010-12-23
Or if you want to see it by default when you boot your PC, you need to comment this line with # in beginning in /etc/default/grub.

```
GRUB_HIDDEN_TIMEOUT=0
```

[https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29](https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29)

If you want further help on that, post the output of this command.

```
cat /etc/default/grub
```

---

