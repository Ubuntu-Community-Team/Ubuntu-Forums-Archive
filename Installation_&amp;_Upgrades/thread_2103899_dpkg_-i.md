---
title: "dpkg -i"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by kanjah on 2013-01-11
hi guyz, am kinda new to ubuntu, i really need help, ave downloaded deb file using
wget [http://www.dmasoftlab.com/cont/download/libltdl3_1.5.24-1ubuntu1_i386.deb](http://www.dmasoftlab.com/cont/download/libltdl3_1.5.24-1ubuntu1_i386.deb)

but if i run 
 dpkg -i libltdl3_1.5.24-1ubuntu1_i386.deb
i get this error
# dpkg -i libltdl3_1.5.24-1ubuntu1_i386.deb 
dpkg: error processing libltdl3_1.5.24-1ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libltdl3_1.5.24-1ubuntu1_i386.deb

any advice?

---

### Post by howefield on 2013-01-11
Have you run the command from the folder containing the .deb package ?

Either move to the folder and run the command or use the full path to the file.

---

### Post by kanjah on 2013-01-12
hi, am running as root, ave tried using find, but i dnt seem to find the deb file

---

### Post by howefield on 2013-01-12
You have marked this as solved, so I guess you are sorted, but if not, your download is probably in the Download folder (the default download folder in Firefox).

In the terminal window type

```
cd ~/Downloads
```

Then run your installation command.

---

