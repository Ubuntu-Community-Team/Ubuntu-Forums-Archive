---
title: "Problem with Minecraft"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by poww_genius on 2011-03-01
Hi. I installed Ubuntu for the first time today and after i Installed Java and try to launch Minecraft.jar i only get this popup:
[http://data.fuskbugg.se/skalman02/_______Minecraft.png](http://data.fuskbugg.se/skalman02/_______Minecraft.png)

How do I fix this? Im really satisfied with Ubuntu but if I cant get this to work I must go back to Windows 7. 

So please help me fix this! Bye.

---

### Post by mcduck on 2011-03-02
Don't try to double click the .jar file, that will only extract it's contents (it's basically a .zip archive).

Instead follow the instructions they have at the Minecraft web site, and either right-click the file and choose to execute it with Java, or start it from a command line with "java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame".

(in the long run you'd probably want to create a shell script to execute that command, and then make a menu launcher that points to that script)

---

