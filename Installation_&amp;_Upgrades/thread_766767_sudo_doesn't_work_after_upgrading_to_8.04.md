---
title: "sudo doesn't work after upgrading to 8.04"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by celsofaf on 2008-04-25
Hello! After I upgraded my work PC from 7.10 do 8.04 (32 bits), sudo stoped working. Here is a sample of what happens:

```
celso@arquitas:~$ sudo su
sudo: unable to resolve host arquitas
```

I didn't change any config files. I'm totaly lost and have no ideas... Any light out there? :D

Thanks in advance!


EDIT: solved after a quick forum search, with a similar procedure like the one in [http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361) .

---

### Post by dannet on 2008-04-25
I have the same problem, it seems like that /etc/hosts has not the right configuration, the problem is that to edit the file you need use sudo :/

---

### Post by Ederico on 2008-04-25
Same problem here!

---

### Post by Anders J on 2008-04-25
Same with me, had to get another computer to get this posted!

---

### Post by mdegerne on 2008-04-25
I solved this by going through System->Administration->Network  I was able to unlock and edit the hosts data through that interface.  Adding the host name to the localhost line solved the sudo issues.

---

### Post by jjacks on 2008-04-25
"I have the same problem, it seems like that /etc/hosts has not the right configuration, the problem is that to edit the file you need use sudo"  This is correct.  To get around having to use sudo, when sudo isn't available, you must reboot to recovery mode and access the file as root with the "nano /etc/hosts" command.

See the following link for more background:

[https://bugs.launchpad.net/ubuntu/+bug/203593](https://bugs.launchpad.net/ubuntu/+bug/203593)

One other thing to remember, the root password is created from the first user installation.  I have lost my admin privileges by trying to change that user access.  I ended up losing sudo again.  Once the first user was given admin privileges again, all was right in the world!

I hope this helps,

Jonathan

---

