---
title: "startup problem after install"
date: 2005-11-09
forum: Installation &amp; Upgrades
---

### Post by gondilon on 2005-11-09
I sucessfully installed unbuntu but when I log in it starts to load and thens freezes up. If I try to change the session it also freezes.  
THe tex from the syslog that Seemed relevant:
localhost:Kernel:[ACPI]: error on cpu0: 40(40)
this problem is fixed!!

---

### Post by Lambert on 2005-11-09
After it finishes booting to the log in screen press ctrl+alt+F1. This will take you to a text console.

You should see a cursor with [COLOR=Gray]ubuntu login[/COLOR]: before it. Try to login here and see if it freezes. if not type the command

```
cat /var/log/syslog
``` 
scroll through the text for the time you tried to log in and it froze and post the output back here.

When you're at the graphical login there's a button titled session. Have you clicked there and chose the "gnome failsafe" option and tried to log in?

---

