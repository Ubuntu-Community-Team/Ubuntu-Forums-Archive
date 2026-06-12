---
title: "Delete Dash Program Icons"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by WilhelmGGW on 2013-10-26
12.04 I installed, uninstalled, and re-installed a program .jar

Now in Dash I have two icons for the program and two for its uninstall program. Each set of icons does the same thing: thus, one of each is superfluous.

Question: How do I delete the two superflous icons from Dash, so I'm left with just one start-program icon and one uninstall icon, both of which working as intended?

Thanks for the help.

---

### Post by fantab on 2013-10-27
Try re-booting your computer.

---

### Post by vanadium on 2013-10-27
Just logging out and logging in might also do the trick.

---

### Post by WilhelmGGW on 2013-10-27
Thanks. But neither rebooting nor logging out/in do the trick. Something more I can try? Thanks again.

---

### Post by vanadium on 2013-10-27
In that case, two different .desktop files pointing to the same item might have been created, e.g. a "program.desktop" and a "program-1.desktop". In such a case, the item would be loaded two times by the dash. You will need to detect the duplicates and delete one. System wide .desktop files reside in /usr/share/applications. User specific .desktop files are in ~/.local/share/applications.

---

### Post by WilhelmGGW on 2013-10-27
Thanks, vanadium. The program icons are not in the system wide .desktop. And I remember the java .jar installation had me check to install for user only, which is what I did. But I can't find the program icons where you wrote.. "User specific .desktop files are in ~/.local/share"  Or maybe I'm not getting the full chain of folders. (I'm not sure what the '~' means.) Can you give that to me, the full chain of folders? ..so I can look there? Thanks so much.

---

### Post by fantab on 2013-10-27
~/.local/share means /home/username/.local/share.

You might also want to look in /usr/share/applications

---

### Post by WilhelmGGW on 2013-10-27
Thanks for all the help. It's fixed! I found the deletions I needed to make in..
/home/username/.local/share/applications

---

