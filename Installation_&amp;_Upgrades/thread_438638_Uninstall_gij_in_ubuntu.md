---
title: "Uninstall gij in ubuntu"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by yinglcs2 on 2007-05-09
Can you please tell me how can i uninstall the gij that comes with ubuntu installation?

$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 (Ubuntu 4.1.2-0ubuntu5)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

---

### Post by IgnorantGuru on 2007-05-10
Your package manager should be able to uninstall it.  But I found that if you want to use sun java, etc., it's best to leave gij installed because OpenOffice is set up to use it.  I don't recall the details but I remember removing it broke something.

If you use Firefox and sun java, then make a symbolic link in your Mozilla Plugins directory /usr/lib/firefox/plugins pointing to usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

Do not copy the plugin to your plugins directory. If you do, Mozilla will crash

---

### Post by yinglcs2 on 2007-05-10
I try to uninstall 'gij'from the package manager, it turns out there are a lot of packages depends on it.

---

