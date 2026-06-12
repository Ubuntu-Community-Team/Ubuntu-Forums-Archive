---
title: "Ubuntu user name help"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by vulcan123 on 2006-06-25
OK, i just got Ubuntu and succesfully installed it and partitioned the hard drive so i can use Windows too. But i forgot the user name i entered during the installation! (i accually have no recolection of it ever asking for a user name, but it must have) ](*,) I don't know what to do because i can't get into Ubuntu without a username and password and i am really reluctant to reinstall it. Can anyone tell me how to fix this problem without reinstalling Ubuntu?

---

### Post by aysiu on 2006-06-25
Reboot into recovery mode.
You'll be root.
Type ```
cat /etc/group
``` You'll see your username in there. Then ```
reboot
``` and select the normal mode.

---

### Post by emarkay on 2006-12-20
OK, but how do you CHANGE it.

The 6.10 alternative disk GAVE me a username of "OEM"....

---

### Post by bapoumba on 2006-12-20
[http://ubuntuforums.org/showpost.php?p=1911374&postcount=10]("http://ubuntuforums.org/showpost.php?p=1911374&postcount=10") ;)

---

### Post by emarkay on 2006-12-20
Thanks!

 I then tried "username" instead of "user name" in the search on a whim and found this one.

[http://www.ubuntuforums.org/showthread.php?p=1911403#post1911403](http://www.ubuntuforums.org/showthread.php?p=1911403#post1911403)

---

