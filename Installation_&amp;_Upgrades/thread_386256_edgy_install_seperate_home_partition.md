---
title: "edgy install seperate home partition"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by STREETURCHINE on 2007-03-16
well i nstalled edgy and like a lot of posts say install home on a seperate partition well i did that .
now the question is how do i back up my xorg.conf when i try i get.


rex@rex-rex:~$ sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
cp: cannot stat `/etc/X11/xorg.conf.backup': No such file or directory
rex@rex-rex:~$ 

any ideas i guess i have to change the command now but what to ?

---

### Post by Kateikyoushi on 2007-03-16
Try man cp and you can see how to use it. cp source destination You need permissions to write that folder so use sudo as well.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by STREETURCHINE on 2007-03-16
ok worked this out sorry folks i was putting the command backwards...ooops

---

