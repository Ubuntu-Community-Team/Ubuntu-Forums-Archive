---
title: "Eclipse &amp; Goole Web toolkit"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by residentevil on 2010-02-18
Hello there

As the title suggest I struggled with installing google web toolkit on Eclipse 3.5 using google guide. 

Eclipse just keep saying
 ```
"Cannot complete the install because one or more required items could not be found.
  Software being installed: Google Plugin for Eclipse 3.5 1.2.0.v200912062003 (com.google.gdt.eclipse.suite.e35.feature.feature.group 1.2.0.v200912062003)
  Missing requirement: Google Plugin for Eclipse 3.5 1.2.0.v200912062003 (com.google.gdt.eclipse.suite.e35.feature.feature.group 1.2.0.v200912062003) requires 'org.eclipse.wst.css.core 0.0.0' but it could not be found" 

```

I am using Ubuntu 9.10 x64 :)
Installed eclipse via apt-get.

---

### Post by alex_kent_18 on 2010-04-24
At first, I did face that same problem. Following are my solution for that;

1. uninstall the eclipse from apt
2. download eclipse for linux from eclpse website 
3. extrat the downloaded archive to a folder
4. double click eclipse file. 
5. install GWT

I hope, this should work for ya.

---

