---
title: "installing java and netbeans"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by btumpps on 2005-06-09
hello ppl. i have downloaded the j2sdk 5.0 update 3 with netbeans 4.1. the file name is jdk-1_5_0_03-nb-4_1-linux.bin. i run the command "sh jdk-1_5_0_03-nb-4_1-linux.bin"
 and it gives the error:
jdk-1_5_0_03-nb-4_1-linux.bin: jdk-1_5_0_03-nb-4_1-linux.bin: cannot execute binary file

what should i do?

edit: the problem has been solved. navigate to the directory which the file is downloaded to. to execute the file, first the installer file's permissions should be changed. it can be done with the command:
chmod 755  jdk-1_5_0_03-nb-4_1-linux.bin

and then, the file itself can be run with the command:
./ jdk-1_5_0_03-nb-4_1-linux.bin

and then the installation begins :D

---

### Post by Pixel on 2005-06-09
You need to mark it as an executable:

```
chmod +x "file name"
```
Without the quotes

That should fix it.

---

