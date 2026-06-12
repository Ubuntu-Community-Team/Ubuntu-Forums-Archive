---
title: "[SOLVED] Corrupted folder"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by solitaire on 2008-02-29
Ive a few folders in "/usr/share/doc/" which i can't delete or get access to

If i do a "ls -all" the folder appears with "?" instead of information

```

?--------- ? ?     ?       ?             ? Crossover-Standard-demo

```

If I try and list the folder I get the following:
```

root@Io:/usr/share/doc# ls crossover*
ls: crossover-standard-demo: Permission denied

```

I've tried to force the removal of the folder

```

root@Io:/usr/share/doc# rm -f crossover-standard-demo 
rm: cannot remove `crossover-standard-demo': Permission denied

```

as you can see i'm doing these as ROOT and I still can't remove the folder.

Can anyone help?

---

### Post by solitaire on 2008-02-29
Looks like i sorted it:

**Reminds self to RTFM!!!**

I ran ```
reiserfsck /dev/sda1 --rebuild-tree -s
```

Took a couple of hours to works it's way through the disk but It removed the Corrupted folders :D

---

