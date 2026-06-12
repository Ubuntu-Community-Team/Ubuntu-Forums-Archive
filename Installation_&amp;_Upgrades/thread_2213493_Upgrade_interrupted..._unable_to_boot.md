---
title: "Upgrade interrupted... unable to boot"
date: 2014-03-26
forum: Installation &amp; Upgrades
---

### Post by dan72 on 2014-03-26
I have run the boot-repair CD and it tells me that the repair was successful and to reboot the machine. Upon reboot, I get the repair console again.

Here is the boot repair output:

[http://paste.ubuntu.com/7160354/](http://paste.ubuntu.com/7160354/)

I would _greatly_ appreciate any help you could provide. If any more information is needed I will provide it to the best of my ability.

---

### Post by Kirboosy on 2014-03-27
Welcome to the forums! :D

If the upgrade didn't finish properly I would assume that you have broken packages on your system. Can you run the following command and tell me what happens?

```
sudo apt-get install --fix-broken
```

Hope that helps!
~Caboose
P.S. If you are getting a repair console boot-repair won't do anything for you because boot-repair is for GRUB. Your GRUB is fine but your Ubuntu install is not.

---

### Post by fantab on 2014-03-27
I have fixed interrupted upgrades with:
```
sudo dpkg --configure -a
```

---

### Post by oldfred on 2014-03-27
```
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/xvda1 during installation
UUID=3decdb95-01d2-4db4-8eaa-d6274ad87769 /               ext4    errors=remount-ro 0       1
# swap was on /dev/xvda5 during installation
UUID=a1aa9f57-e706-4ec3-9a65-95cac7be2f8a none            swap    sw              0       0
/var/log/ispconfig/httpd/test.followthehorizon.com /var/www/clients/client0/web4/log    none    bind,nobootwait    0 0
/var/log/ispconfig/httpd/followthehorizon.com /var/www/clients/client0/web1/log    none    bind,nobootwait    0 0
/var/log/ispconfig/httpd/renthaven.org /var/www/clients/client0/web5/log    none    bind,nobootwait    0 0
/var/log/ispconfig/httpd/startexploring.org /var/www/clients/client0/web6/log    none    bind,nobootwait    0 0


```
I do not know bind type mounts, but are those correct? And are they still there after your upgrade?

---

