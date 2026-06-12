---
title: "Root Password......"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by godsownman on 2005-07-11
I am using Ubuntu Linux.

Can anybody please tell me how to access / log into the root section  .

When I had installed the OS I was not asked for setting a username and password thats why I am wondering.( I dont know what USER AND PASS to use ! )

I was just exploring many parts of the OS today and It keeps telling me that you are not the owner , login as root.

For eg. I was trying to change the permissions for mounting ( hd0) c:  but when I went to that following this path

/dev/hd0  

and right clicked -> properties and tried it I was told that you are not the owner.Root is the owner and hence I could not mount it.

Thanks for your time and patience.

---

### Post by Leif on 2005-07-11
wiki.ubuntu.com//RootSudo

---

### Post by godsownman on 2005-07-11
Can somebody also help me as to how I should mount my Windows c: into linux and vice versa into Windows.

---

### Post by brim4brim on 2005-07-11
Here are some links to help with starter issues, your problem is answered in both but I recommend the ubuntuguide.org for your issue:

[http://ubuntuforums.org/showthread.php?t=31094&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=31094&page=1&pp=10)

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by doom_Oo7 on 2005-07-11
[QUOTE=godsownman]Can somebody also help me as to how I should mount my Windows c: into linux and vice versa into Windows.[/QUOTE]
 to mount : 
1st, go root
2nd, make a directory on /mnt/
Call it partc for exemple
in console :

mount -t [filesystem type, generally fat, fat32 or ntfs] /dev/[name of peripheral, if it's c: it's certainly hda1] /mnt/[the directory you just made]

And well, that's it :)

NOTE : you can make the directory everywhere :)

---

