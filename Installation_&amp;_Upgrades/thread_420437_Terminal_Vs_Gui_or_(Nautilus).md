---
title: "Terminal Vs Gui or (Nautilus)"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by TFildes on 2007-04-23
I am running a bare install of Ubuntu 7.04 64 bit. There seems to be a difference between a Directory created in Nautilus vs one created in Terminal. When entering terminal I type DIR and it shows the folders. But when I type CD Download for example it tells me bad command or filename more or less. The Download folder was created in Nautilus. It lists in terminal but will not let me change to it. When I delete the folder and recreate it in the terminal it lists it both in Nautilus and terminal and now terminal will let me change to it typing the same command. What gives????

---

### Post by tgm4883 on 2007-04-23
Have you tried cd Download?

cd != CD

---

### Post by obijywk on 2007-04-23
maybe it's some sort of permissions problem.... what do you see when you type 'ls -l'? is there any difference in the permission flags between folders created in terminal and folders created in nautilus?

---

### Post by bulldog on 2007-04-23
Linux makes a difference between cd and CD.
Uppercase and lowercase aren't the same.
cd Download is different as cd download
Windows doesn't.

---

