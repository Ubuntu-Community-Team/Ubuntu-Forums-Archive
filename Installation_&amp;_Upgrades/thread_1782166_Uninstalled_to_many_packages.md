---
title: "Uninstalled to many packages"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by Johnsen9000 on 2011-06-14
I tried to uninstall one of the dictonaries, because i have two and i really don't need two. nothing would show up in software center, so i made it show hidden pachages. then i saw something that i think was called gnu dictonary. i tried to uninstall that and see if one of the dictonaries would be uninstalled, but instead, nothing works except a few programs, like internett,synaptic package manager and ubuntu update.

software center has dissapeard, and,i guess, alot of the other standard gnu programs have dissapeard. real info can i give you to help me fix this?

---

### Post by mörgæs on 2011-06-14
This is my best guess, but I am not sure. Do it only if you have a backup.

You could try 

```
sudo apt-get install xubuntu-desktop
```

---

### Post by Johnsen9000 on 2011-06-14
i found software package in the synaptic package manager, so i installed most of the other softwares i needed again. but i have two dictionaries.

any idea how to remove at least one of them?

---

### Post by mörgæs on 2011-06-14
Sorry, I don't know.

By the way, why do you want to remove them? Are they big?

---

### Post by Toz on 2011-06-14
> **Johnsen9000 said:**
> i found software package in the synaptic package manager, so i installed most of the other softwares i needed again. but i have two dictionaries.

any idea how to remove at least one of them?

I think we need to first identify the dictionary packages. By default, xubuntu comes with xfce4-dict. Open a terminal window (Accessories->Terminal Emulator), type in the following command, and post back the results:```
ls -l /usr/share/applications/ | grep -i dict
```

Hopefully you will have more than one entry. If we can properly identify the second dictionary package, we can advise on proper removal procedures.

---

### Post by Johnsen9000 on 2011-06-15
No,they are probably not big at all. I've only uninstalled alot of programs i really don't need. If i at one point need them,then i will install them. And two programs that do the same thing, a thing that i don't even wan't, is in my mind stupid. but that is of course not your fault. it's what happends when you install xfce on ubuntu. you get two versions of alot of programs. so it's just up to me to clean it up. Thanks for the help of course.

the terminal said:
```
-rw-r--r-- 1 root root   485 2011-04-19 22:42 gnome-dictionary.desktop
-rw-r--r-- 1 root root  3810 2011-01-04 23:34 xfce4-dict.desktop
```

What next?

---

### Post by Toz on 2011-06-15
The easy fix (to hide the menu item) would be to edit the file /usr/share/applications/gnome-dictionary.desktop:```
gksudo gedit /usr/share/applications/gnome-dictionary.desktop
``` and edit the line:```
NoDisplay=false
``` to read:```
Nodisplay=true
```

If the NoDisplay entry does not exist, then add the line at the end:```
NoDisplay=true
```

---

### Post by Johnsen9000 on 2011-06-18
what would happend if i just uninstall one?

---

### Post by Toz on 2011-06-18
Isn't that what led to your original problem? Perhaps the best is to just hide the one you don't want.

---

### Post by Johnsen9000 on 2011-06-19
i didn't uninstall one of these dictonaries, i uninstalled something i thought was the dictonary. And the fact that i showed hidden packages is probably another error. Anyway,all i had to do was to install the software center again. then install the ekstra programs that may have been uninstalled. it set me back 30min max.

anyway, i risk it,aaaaaand
no problem

went to softaware center, searched for gnome dictonary, and uninstalled. since i have xfce, then i don't need gnome dictonary....

but thanks for the help to find it though...

---

