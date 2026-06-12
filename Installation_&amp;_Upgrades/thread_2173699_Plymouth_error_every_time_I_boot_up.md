---
title: "Plymouth error every time I boot up"
date: 2013-09-10
forum: Installation &amp; Upgrades
---

### Post by PopsTheSailor on 2013-09-10
Every time I boot up, I get a pop-up that says "System Problem Detected". I click on report problem and after enter the admin password I get a button to show details. When I click on it I get the following. I can't copy & paste so these are the things that seem important to me:

ExecutablePath
     /sbin/plymouthd

Package
     plymouth 0.8.8-0ubuntu6.2

Problem Type
     Crash

Title
     plymouthd crashed with SIGSEGV in script_obj_deref_direct()

ApportVersion
     2.9.2-0ubuntu8.3

Any ideas on how to fix this or is there a way to reinstall plymouth?

---

### Post by deadflowr on 2013-09-11
You can find the full text in a file in the folder /var/crash.

Secondly, after you click to report it, does anything else happens, like a more information needed or a web browser opens.
Plus, which version of ubuntu?

Though copying the line
 [COLOR=#000000]plymouthd crashed with SIGSEGV in script_obj_deref_direct()

into my browser search came across plenty of varying bug reports.

[/COLOR]

---

### Post by PopsTheSailor on 2013-09-11
I'm using 13.04. Should have mentioned that.
I'll search on the plymouthd crashed line. I wasn't really sure what I should key in on when searching for a fix.

---

