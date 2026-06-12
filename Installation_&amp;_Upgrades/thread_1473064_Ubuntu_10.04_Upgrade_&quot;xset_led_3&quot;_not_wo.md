---
title: "Ubuntu 10.04 Upgrade &quot;xset led 3&quot; not working"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by Louis Cypher on 2010-05-04
I recently upgraded to 10.04 Lucid.  Before I had the command "xset led 3" mapped to my scroll lock button.  This turned on the SunbeamTech Illuminated Keyboard.  Now it does nothing even when typing it into the terminal.  Has anyone had this problem after upgrading?  Thx

---

### Post by SkeLLLa on 2010-05-06
> **Louis Cypher said:**
> I recently upgraded to 10.04 Lucid.  Before I had the command "xset led 3" mapped to my scroll lock button.  This turned on the SunbeamTech Illuminated Keyboard.  Now it does nothing even when typing it into the terminal.  Has anyone had this problem after upgrading?  Thx

This probles seems also have been in karmic. I fix it with:
```
xmodmap -e 'add mod3 = Scroll_Lock'
```
But it's only for current session.

---

### Post by Louis Cypher on 2010-05-06
SkeLLLa, Thanks a ton!  This worked for me as well.

---

