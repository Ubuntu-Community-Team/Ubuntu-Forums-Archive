---
title: "Remove previous menu item for netbeas"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by shantha on 2010-12-19
Hi,

I installed NetBeans 5.5.1, then upgraded ubuntu and installed NetBeans 6.5.1.
Finally I upgraded to Ubuntu 10.10 and installed NetBeans 6.8.

I tried to uninstall those unwanted previous versions of NetBeans using
```
:~$ sudo apt-get --purge remove netbeans5.5
```
```
:~$ sudo apt-get --purge remove netbeans6.5
```

But it gives message
```
:~$ sudo apt-get --purge remove netbeans5.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package netbeans5.5 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The problem is there is no installed version of NetBeans 5.5.1 and 6.5.1 but there are two menu items 

[LIST]
[*] Applications -> Programming ->NetBeans 5.5.1
[*]Applications -> Programming ->NetBeans 6.5.1
[/LIST]
Can anybody help me on this regards to remove those menu items from the system with remaining files if there is any?

Regards,
Shantha.

---

### Post by sikander3786 on 2010-12-19
Welcome to the forums :-)

What happens when you click those menu entries? Nothing I hope.

If they are just menu entries (as the program is not installed any more), go to System > Administration > Main Menu and tweak the Menus accordingly.

---

### Post by shantha on 2010-12-24
Thanks for the reply.

It worked for me.

The path is bit different in my system.
System -> Preferences -> Main Menu.

Hope there is no affect to the system by just deleting those items. I assume there is no remaining files or any settings relevant to them.

Regards,
Shantha.

---

