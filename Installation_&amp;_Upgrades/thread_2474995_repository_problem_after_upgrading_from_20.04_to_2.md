---
title: "repository problem after upgrading from 20.04 to 22.04"
date: 2022-05-13
forum: Installation &amp; Upgrades
---

### Post by akashsinhaha on 2022-05-13
[COLOR=#232629][FONT=-apple-system]I upgraded from 20.04 (focal) to 22.04 (jammy) and in the [/FONT][/COLOR]sources.list.d[COLOR=#232629][FONT=-apple-system] folder it is still showing some files with focal in them. Should I change them to jammy manually?
here is a screenshot.
[/FONT][/COLOR][IMG]https://i.stack.imgur.com/c67WD.png[/IMG]

---

### Post by Tadaen_Sylvermane on 2022-05-13
First.  Copy / paste in code tags. Not everyone has the same bandwidth for pictures. Common courtesy.

That being said a proper upgrade upgrades Ubuntu. Not the ppa's because it can't know how many one has. You need to do those yourself.

---

### Post by deadflowr on 2022-05-13
You don't need to do anything as the file should not be read by apt.
It's just a backup file from when the release upgrade was done.
Is apt showing output from the file?

If it concerns you can just delete it.

---

