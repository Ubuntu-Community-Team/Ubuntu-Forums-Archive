---
title: "Installing .deb packages"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by nuveena on 2011-03-05
[COLOR=black][FONT=Times New Roman]How can I install this package correctly.[/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman]used ubuntu 10.10[/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman]I downloaded gramps_3.2.5-1_ubuntu10.deb in other computer. I copied it to desk top of my computer. Then I write code sudo dpkg -i gramps_3.2.5-1_ubuntu10.deb [/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]I have a message [/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]nuveena@ubuntu:~$ sudo dpkg -i gramps_3.2.5-1_ubuntu10.deb [/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][sudo] password for [/FONT][/COLOR]**[COLOR=red][FONT=Times New Roman]nnnnnnn[/FONT][/COLOR]**[COLOR=black][FONT=Times New Roman]: [/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman]dpkg: error processing gramps_3.2.5-1_ubuntu10.deb (--install): [/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman]cannot access archive: No such file or directory [/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman]Errors were encountered while processing: [/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman]gramps_3.2.5-1_ubuntu10.deb [/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman]nuveena@ubuntu:~$ [/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]How can I install this package correctly.[/FONT][/COLOR]

---

### Post by jeremyjjbrown on 2011-03-05
You should just be able to launch a .deb from Nautilus. You don't need to access it from the terminal. Just double click it. It should do the rest or it's probably corrupt.

---

### Post by nuveena on 2011-03-05
What is  Nautilus.  I am new  to  Ubuntu.
Thanks

---

### Post by wojox on 2011-03-05
When your in the terminal you need to **cd Desktop** and move to that directory and run your commands again.

---

### Post by beew on 2011-03-05
If you just right click it it the software center should show up and offers to install it, but I prefer to use gdebi to install deb files by right clicking (much faster than  SC for less overhead). Since gdebi is no longer installed by default you have to install it using Synaptic first.

If you want to use the command line like you did you have to get to the folder where the .deb file is before you run the dpkg command.

So if you save the file on the desktop you have to first
```

cd Desktop
```note the capital D. Without that Ubuntu assumes the file is in Home/username and you get the error message because the file is not there.

(if you save the file in another location you would have to change to that location first, like cd Downloads, etc. But if you save the file in Home/username then you don't have to issue any cd command because the file is already in your default directory,--cd means change directory)

EDITED: Just saw that WOJOX already pointed out you forgot the cd command.

---

### Post by jeremyjjbrown on 2011-03-05
> **nuveena said:**
> What is  Nautilus.  I am new  to  Ubuntu.
Thanks

Nautilus is Gnome's version of explorer.exe, it's how you browse your files and folders in Ubuntu.

---

### Post by nuveena on 2011-03-07
Thanks  all of you .you wasting  your  time  for  me. 
 
 
jeremyjjbrown  :D
wojox  :D
beew    :D

---

### Post by nuveena on 2011-03-07
> **beew said:**
> If you just right click it it the software center should show up and offers to install it, but I prefer to use gdebi to install deb files by right clicking (much faster than SC for less overhead). Since gdebi is no longer installed by default you have to install it using Synaptic first.
 
If you want to use the command line like you did you have to get to the folder where the .deb file is before you run the dpkg command.
 
So if you save the file on the desktop you have to first
```

cd Desktop
```note the capital D. Without that Ubuntu assumes the file is in Home/username and you get the error message because the file is not there.
 
(if you save the file in another location you would have to change to that location first, like cd Downloads, etc. But if you save the file in Home/username then you don't have to issue any cd command because the file is already in your default directory,--cd means change directory)
 
EDITED: Just saw that WOJOX already pointed out you forgot the cd command.
 So much Thanks  for you . I learn lot of things  about ubuntu.         :lolflag:

---

### Post by nuveena on 2011-03-07
> **wojox said:**
> When your in the terminal you need to **cd Desktop** and move to that directory and run your commands again.
 Thank you  so much .:lolflag:

---

