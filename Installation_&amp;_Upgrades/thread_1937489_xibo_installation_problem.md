---
title: "xibo installation problem"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by Ericyue on 2012-03-07
hi, i try to install the xibo server on my ubuntu, but i meet a problem when extract.

the install guild ([http://wiki.xibo.org.uk/wiki/Install_Guide_Xibo_Server](http://wiki.xibo.org.uk/wiki/Install_Guide_Xibo_Server)) 
says that i nid to move my xibo-server-1.2.2.1.tar.gz to the /var/www (i do that)

and after that, i use the command in the guild ->  sudo tar zxvf ~/xibo-server-1.2.2.1.tar.gz

but it give me some error problem ->

root@pc-main-desktop:/var/www# sudo tar zxvf ~/xibo-server-1.2.2.1.tar.gz
tar: /root/xibo-server-1.2.2.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

can anyone know what is the problem ??

---

### Post by Toz on 2012-03-08
Its not finding the file because you have moved it to /var/www and you are referencing it in your home (~) directory. After you move the file to /var/www, try this:
```

cd /var/www
sudo tar zxvf xibo-server-1.2.2.1.tar.gz

```

---

### Post by Ericyue on 2012-03-08
i got it .. thanks a lot for your help :):D:D:D:D

---

