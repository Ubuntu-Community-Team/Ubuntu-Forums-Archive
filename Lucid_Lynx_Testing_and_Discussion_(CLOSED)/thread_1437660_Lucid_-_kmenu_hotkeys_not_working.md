---
title: "Lucid - kmenu hotkeys not working"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by genux05 on 2010-03-24
Hi all,

I have just upgraded to lucid (great btw, it works just really well and impressed already).

But there is a problem with the kmenu editor with the hotkeys

If you edit a shortcut key
rightlclick K menu -> mnenu Editor -> firefox -> advanced tab -> current shortcut key

and save, it does not work.. any advice ?

---

### Post by genux05 on 2010-03-24
I installed kubuntu 9.10 and found out the difference between one that was working and one that was not e.g. in 10.4 lucid

if you look in the file ~/.kde/share/config/khotkeysrc and make sure that the values Enabled are true instead of false for the Data_1 and Data_1_1 then it will work as below

[Data_1]
Comment=KMenuEdit Global Shortcuts
DataCount=6
Enabled=true
Name=KMenuEdit
SystemGroup=1
Type=ACTION_DATA_GROUP

[Data_1Conditions]
Comment=
ConditionsCount=0

[Data_1_1]
Comment=Comment
Enabled=true

to update the configuration settings you just need to 

qdbus org.kde.kded /modules/khotkeys reread_configuration

---

### Post by SushiR on 2010-03-25
Thank you, works like a charm :-)

---

