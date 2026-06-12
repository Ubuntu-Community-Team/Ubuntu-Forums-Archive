---
title: "Azureus not working after upgrading!"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by iceclow on 2006-06-04
Well after dealing with my broadcom wifi card and dapper new modules, I try to start Azureus and I discover that it doesn work! This the output message:

ice@ICE:~$ azureus
Starting Azureus...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_06]
Configuring environment...
Loading Azureus:
java -Xms16m -Xmx128m -cp "/usr/bin/*.jar" -Djava.library.path="/usr/bin" -Dazureus.install.path="/usr/bin" org.gudy.azureus2.ui.swt.Main ''
Exception in thread "main" java.lang.NoClassDefFoundError: org/gudy/azureus2/ui/swt/Main
Azureus TERMINATED.

It worked well in breezy. What I can do? 

Thanks in advance.

---

### Post by wr0x2 on 2006-06-06
Azureus completely broke after I upgraded. Now I can't find it anywhere and the command returns as not found. Anyone think this is related?

EDIT: Saw [this]("http://ubuntuforums.org/showthread.php?t=188825&highlight=Azureus") thead.

---

