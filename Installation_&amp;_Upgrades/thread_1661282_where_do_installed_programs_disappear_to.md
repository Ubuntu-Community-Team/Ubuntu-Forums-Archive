---
title: "where do installed programs disappear to?"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by JoeYsUn on 2011-01-06
[FONT=Comic Sans MS]Sometimes i install programs and they just disappear... i'm told they're installed but they're invisible to me... How can i find them? is there something like "windowsexplorer" where i can find all the installed stuff?
thanks[/FONT]

---

### Post by welwitschia on 2011-01-06
Can you describe in more detail what happened?

---

### Post by oldos2er on 2011-01-06
Which programs? If they're CLI apps, they won't have a menu entry.

You can see where each file in a package is installed with ```
dpkg -L <package name>
```

---

