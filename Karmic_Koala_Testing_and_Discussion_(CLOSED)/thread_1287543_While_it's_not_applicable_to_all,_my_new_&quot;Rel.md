---
title: "While it's not applicable to all, my new &quot;Reloading Ubuntu 9.10&quot; &quot;Cheat Sheet&quot;"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-10
Something that I have evolved over a few years and it has GREATLY assisted in reloading and for reference - Of course this one is also "Still in Beta"
Feel free to grab and modify as needed.
A little something in return to all!  :)

---

### Post by smCw6GNakQn300£ on 2009-10-12
While completely re-installing my PC (Windows 7 and Ubuntu 9.04) for work recently, I did the following small, but very handy step, to very quickly re-install all the ubuntu apps I had previously:

- BEFORE uninstalling/reinstallation
     - ```
dpkg --get-selections > installed_apps
```
     - keep a copy of the *installed_apps* file for use later
     - backup the **sources.list** file from */etc/apt* for use later


- AFTER installation
     - copy the saved **sources.list** into */etc/apt*
     - ```
sudo dpkg --set-selections < installed_apps
```
     - ```
sudo apt-get dselect-upgrade
```

This should now go and select, then install all the apps you had listed in your file.
Saves a lot of individual installing.

---

### Post by setherd on 2009-10-12
Cool! some good tips in there.
out of curiosity why do you uninstall all bluetooth stuff??

---

### Post by emarkay on 2009-10-12
> **setherd said:**
> Cool! some good tips in there. Out of curiosity why do you uninstall all bluetooth stuff??

 Don't have any Bluetooth devices!  Thanks - I've had this evolving since Hardy.

I had "Evolution" in there too to remove, in Jaunty,  but wanted to try it out in Karmic - to me it's still redundant with Thunderbird so I am adding it back in.  
Also added "create-resources" to the "Add (as desired:" list, "Unrar" is already installed with the "Restricted Drivers", and "Google Earth" is now an "Add Programs:" (outside of Synaptic) category. There are also a few minor typos.  

I'll post the revised page when I finish testing Karmic with the the NVIDIA PC.

---

### Post by 23meg on 2009-10-12
Please replace all instances of "sudo gedit" with "[gksudo gedit]("https://help.ubuntu.com/community/RootSudo#Graphical%20sudo")".

---

### Post by sdowney717 on 2009-10-12
sources.lst should be called sources.list ?

---

### Post by emarkay on 2009-10-12
> **23meg said:**
> Please replace all instances of "sudo gedit" with "[gksudo gedit]("https://help.ubuntu.com/community/RootSudo#Graphical%20sudo")".

I had NEVER known this!  THANKS! 

Posted for all in "General Help"
[http://ubuntuforums.org/showthread.php?p=8093023#post8093023](http://ubuntuforums.org/showthread.php?p=8093023#post8093023)

---

### Post by emarkay on 2009-10-12
> **sdowney717 said:**
> sources.lst should be called sources.list ?

I don't have that anywhere on the sheet, but but it is "sources.list"

[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html)

---

### Post by smCw6GNakQn300£ on 2009-10-12
> **emarkay said:**
> I don't have that anywhere on the sheet, but but it is "sources.list"

[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html)

sorry - my bad.
Post updated to show "sources.list"

---

### Post by emarkay on 2009-10-16
Updated at "Freeze", should be good for the next 6 months.  :)

---

