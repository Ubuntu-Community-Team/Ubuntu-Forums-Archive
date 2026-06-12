---
title: "synaptic upgrade"
date: 2006-05-10
forum: Installation &amp; Upgrades
---

### Post by paparucino on 2006-05-10
Hi guys
I ugraded from 5.10 to 6.04. It's fine but I don't find anywhere the synaptic upgrader. It was very helpful for me. 
Where is it now? I need it! :-)

---

### Post by PhrankDaChickenGeek on 2006-05-10
Should be in "System -> Administration -> Update Manager"

---

### Post by linuxcity on 2006-05-10
I could not find that in there neither, but you can use the "termina"l to update your system to the latest available package: 

"Applications | Accessories| Terminal"

sudo apt-get update
sudo apt-get upgrade or sudo apt-get dist-upgrade

---

### Post by Sef on 2006-05-10
If your update manager is missing or other packages are, type these commands from the terminal:

sudo apt-get update

sudo apt-get install ubuntu-base unbuntu-desktop

sudo apt-get dist-upgrade

It worked for me.

---

### Post by paparucino on 2006-05-11
[QUOTE=Sef]If your update manager is missing or other packages are, type these commands from the terminal:

sudo apt-get update

sudo apt-get install ubuntu-base unbuntu-desktop

sudo apt-get dist-upgrade

It worked for me.[/QUOTE]
I tried all your commands, they were successfull, but I don't get the option in "System"

---

### Post by Gustav on 2006-05-11
Do you mean the "synaptic package manager" (the package management program), the "update manager" (the program that usually handles updates) or the "update-notifier" (the little icon that pops up when you have updates)?

---

### Post by paparucino on 2006-05-11
[QUOTE=Gustav]Do you mean the "synaptic package manager" (the package management program), the "update manager" (the program that usually handles updates) or the "update-notifier" (the little icon that pops up when you have updates)?[/QUOTE]
The first one. I see it in Alacarte Menu Editor but not in System Administration.  I tried to to check/uncheck it in Alacarte but nothing happens

---

### Post by Gustav on 2006-05-12
can you run it by typing```
gksudo synaptic
```it a terminal?

---

### Post by paparucino on 2006-05-12
[QUOTE=Gustav]can you run it by typing```
gksudo synaptic
```it a terminal?[/QUOTE]
yeah, I know. I've done a link on the application bar, but I liked in the system pop up. Ok

---

