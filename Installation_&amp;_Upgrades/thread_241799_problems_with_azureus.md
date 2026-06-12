---
title: "problems with azureus"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by s1k3st on 2006-08-22
Every time Azureus crashes (like when I change icons...) this warning pops up when I run it the next time and you can't close it! I read somewhere the new version fixes this. So, how is it possible to update to the new version?

---

### Post by royale on 2006-08-23
Go to this page and download the latest jar file to your desktop. 

[http://azureus.sourceforge.net/download.php]("http://azureus.sourceforge.net/download.php")

rename it to "Azureus2.jar".

Close Azureus, then do
```

sudo cp /usr/share/java/Azureus2.jar /usr/share/java/Azureus2.jar.backup
sudo cp ~/Desktop/Azureus2.jar /usr/share/java/Azureus2.jar
```

That will update you to the latest jar file, and next time you get that popup  the buttons on it should respond correctly.

Good luck!

---

