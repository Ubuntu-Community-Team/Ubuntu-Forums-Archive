---
title: "i didnt get how do i create an archive packages (tar, gz, deb)"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by dinbrca on 2008-06-21
how do i create an archive packages..?
i started to learn how to archive files from:
[http://www.linux.org/lessons/beginner/l15/lesson15a.html](http://www.linux.org/lessons/beginner/l15/lesson15a.html)
i first created a txt file and then i got into the directory where the text file is and then i entered:
tar -cvf *.txt
and it says:
"
tar: Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.
"
what should i do now?

---

### Post by Kevbert on 2008-06-21
```
tar cf file.tar myfile.txt  
```
Create a tar file called file.tar containing myfile.txt or
```
tar czf file.tar.gz myfile.txt  
```
Create a tar file called file.tar.gz (with gzip compression) containing myfile.txt

---

### Post by dinbrca on 2008-06-21
and create deb?
dpkg -b file.deb *
?

---

### Post by Kevbert on 2008-06-21
Yes, but have a look at [this]("http://www.linuxdevices.com/articles/AT8047723203.html") first.

---

