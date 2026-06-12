---
title: "Error in Registry?"
date: 2013-08-02
forum: Installation &amp; Upgrades
---

### Post by tfyMMRA on 2013-08-02
Every time I try to install Ubuntu alongside Windows using Wubi, I receive this error message, [http://imgur.com/bgzrod0](http://imgur.com/bgzrod0) and the file in question looks like this in notepad: [http://pastebin.com/2ATm9Ffk](http://pastebin.com/2ATm9Ffk)

Any help?

---

### Post by dgharmon on 2013-08-02
Delete the contents of C:\ubuntu\* and try again ...

---

### Post by tfyMMRA on 2013-08-02
I just did, and it gave me the same error again.

---

### Post by Karlchen on 2013-08-03
Hello, tfyMMRA.

> Every time I try to install Ubuntu alongside Windows using Wubi, I receive this error message, [http://imgur.com/bgzrod0](http://imgur.com/bgzrod0) and the file in question looks like this in notepad: [http://pastebin.com/2ATm9Ffk](http://pastebin.com/2ATm9Ffk) Have you made sure that you right-clicked wubi.exe and selected "Run as administrator" from the contect menu? You must run wubi.exe in elevated mode. Else it will not be able to add the Ubuntu startup entry to the Windows boot menu.

Kind regards,
Karl

---

### Post by bcbc on 2013-08-03
You need to rebuild your BCD: 
[http://windows.microsoft.com/en-ca/windows7/windows-7-windows-server-2008-r2-service-pack-1-sp1-installation-error-0x800f0a12](http://windows.microsoft.com/en-ca/windows7/windows-7-windows-server-2008-r2-service-pack-1-sp1-installation-error-0x800f0a12)

---

