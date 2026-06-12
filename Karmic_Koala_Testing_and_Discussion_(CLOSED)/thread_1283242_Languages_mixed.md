---
title: "Languages mixed"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Miguel on 2009-10-05
Hello again,

I had a suspend failure today on karmic and, a while later (I had lunch), after the reboot I noticed how Gnome mixes my languages. I have both english and spanish support installed, and the system default for everybody is spanish. However, some applications are in english while they were in spanish before. For example, nautilus is in spanish, while gnome-terminal and Gimp are in english (Gimp was in english this morning before the crash, though). 

I attach a screenshot showing the top left menu (Applications, Places, System) in english with nautilus in spanish ("Archivo, Editar, Ver" instead of "File, Edit, View").

I have tried the following things:[list]
[*] Checking the language on a terminal returns spanish:
```

$ echo $LANG
es_ES.UTF-8

```
[*] Logging out and in as a new user (doesn't help)
[*] Reinstalling language-support-es and language-support-en-base
[/list]
However, none of this helped. Does anybody have a clue? Is anybody else experiencing anything similar?

---

### Post by dalonso on 2009-10-05
> **Miguel said:**
> Hello again,

I had a suspend failure today on karmic and, a while later (I had lunch), after the reboot I noticed how Gnome mixes my languages. I have both english and spanish support installed, and the system default for everybody is spanish. However, some applications are in english while they were in spanish before. For example, nautilus is in spanish, while gnome-terminal and Gimp are in english (Gimp was in english this morning before the crash, though). 

I attach a screenshot showing the top left menu (Applications, Places, System) in english with nautilus in spanish ("Archivo, Editar, Ver" instead of "File, Edit, View").

I have tried the following things:[list]
[*] Checking the language on a terminal returns spanish:
```

$ echo $LANG
es_ES.UTF-8

```
[*] Logging out and in as a new user (doesn't help)
[*] Reinstalling language-support-es and language-support-en-base
[/list]
However, none of this helped. Does anybody have a clue? Is anybody else experiencing anything similar?

Hi Miguel,

this is currently being discussed in this thread: [http://ubuntuforums.org/showthread.php?t=1282749](http://ubuntuforums.org/showthread.php?t=1282749)

A bug has been opened:

[https://bugs.launchpad.net/ubuntu/+source/language-pack-es/+bug/443101](https://bugs.launchpad.net/ubuntu/+source/language-pack-es/+bug/443101)

Go there and click the link "This bug affects me too".

---

### Post by Miguel on 2009-10-05
Thanks! I did a quick search on launchpad, but didn't find anything meaningful.

---

