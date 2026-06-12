---
title: "install windows software in wine"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by 123my on 2007-10-07
I have install wine in my Ubuntu. How can I install Windows software(which is nto install yet) in Ubuntu?

---

### Post by FunkyJack on 2007-10-07
Run setup (probably Setup.exe) file with wine and it will install in:
/home/your_user/.wine/c_drive/Program Files/

---

### Post by Cannaregio on 2007-10-07
_In some cases_ you don't even need to install through wine, you can just copy a complete folder, with the windows application files and subfolders, somewhere on your box and then just start it through wine.

A case I experienced is JTTrainDriver ([http://www.gamespot.com/pc/sim/traindriver/index.html]("http://www.gamespot.com/pc/sim/traindriver/index.html")): a very nice rail simulation. You just copy somewhere everything and his dog:
```
-rw-r--r--  1 root   root    654152 2007-10-07 11:24 assets.tdx
drwx------  5 lopper root      4096 2006-03-08 17:51 Bin
drwx------  8 lopper root      4096 2007-10-07 11:32 Cache
drwx------ 18 lopper root      4096 2006-03-08 17:50 Data
drwx------  3 lopper root      4096 2006-03-08 17:50 Docs
drwx------  2 lopper root      4096 2006-03-08 17:50 editing
-rwx------  1 lopper root    131334 2007-10-07 11:27 JetLog.txt
-rwx------  1 lopper root     40960 2005-10-07 10:40 JTTrainDriver.exe
drwx------  2 lopper root      4096 2006-03-08 17:50 Libraries
-rw-r--r--  1 lopper lopper       0 2007-10-07 11:57 list.txt
drwx------  2 lopper root      4096 2006-03-08 17:50 Local
-rwx------  1 lopper root   1060864 2005-10-07 10:34 MFC71.dll
-rwx------  1 lopper root    348160 2005-10-07 10:34 msvcr71.dll
-rwx------  1 lopper root     16906 2005-10-07 10:34 readmeback.jpg
-rwx------  1 lopper root      7060 2005-10-07 10:34 readme.htm
-rwx------  1 lopper root     40594 2005-10-07 10:34 readmelogo.gif
drwx------  2 lopper root      4096 2006-03-08 17:50 Regs
drwx------  2 lopper root      4096 2006-03-08 17:50 Scripts
drwx------  2 lopper root      4096 2007-10-07 11:27 Settings
drwx------  2 lopper root      4096 2006-03-08 17:50 Tmp
-rwx------  1 lopper root   1892664 2005-10-11 10:16 trains.ja
-rwx------  1 lopper root        52 2007-10-07 11:32 Trainz.cfg
-rwx------  1 lopper root       115 2005-10-07 10:34 trainzoptions.txt
drwx------  2 lopper root      4096 2006-03-08 17:50 Video
drwx------  5 lopper root      4096 2006-03-08 17:43 World

```

and when you then open ```
JTTrainDriver.exe
``` with wine, it will run without any prior "wine installation".

_In most cases,_ you just install everything using wine, and what you installed will be in the virtual c:/drive that wine will have created. I had very good experiences with "poser 7", a 3D application that not only runs perfectly through wine in gutsy beta, but also renders waay more quickly as in windows xp. Probably because it is not phoning home all the time in the wined linux environment :-)

So you can try both approaches.

---

