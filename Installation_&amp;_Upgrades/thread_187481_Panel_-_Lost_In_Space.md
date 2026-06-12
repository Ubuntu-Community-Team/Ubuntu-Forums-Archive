---
title: "Panel - Lost In Space"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by mpierce on 2006-06-03
Upgraded kubuntu the lazy way to drapper using Adept.

Have fixed most things but the KDE panel is gone. By that I mean there is no start button, icons, etc. 

How do I fix this?
I'm doing everything from CLI.

---

### Post by snds24 on 2006-06-03
Try Alt+F2 and write : kicker

---

### Post by henriquemaia on 2006-06-03
[quote=mpierce]Upgraded kubuntu the lazy way to drapper using Adept.

Have fixed most things but the KDE panel is gone. By that I mean there is no start button, icons, etc. 

How do I fix this?
I'm doing everything from CLI.[/quote]

Backup you kde folder and remove it. Like this:

```
cp ~/.kde ~/Desktop/kde_backup
```

then:

```
rm -r ~/.kde
```

After this, restart your session. You can do ctrl+alt+backspace. 
 

If this works, than you can import some configurations you need from the older kde folder you made a backup copy, by putting them on the newly created ~/.kde folder.

Maybe this helps out.

---

