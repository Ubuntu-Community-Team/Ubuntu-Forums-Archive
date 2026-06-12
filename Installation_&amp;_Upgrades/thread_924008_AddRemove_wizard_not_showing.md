---
title: "Add/Remove wizard not showing"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by deepaksinghkushwah on 2008-09-19
Hi all, i have a little problem. I hope u all will help me. I have installed ubuntu 10 days ago. that was first time i use it. I was trying to install some software using add/remove program manager in applications. but it was showing the error to use synaptic to install new software. that's why i try to remove synaptic. I use "sudo apt-get remove synaptic" command. but it remove add/remove manger too. now i m unable to use this wizard. is there any option that i can reinstall the add/remove wizard and remove synaptic manager. 

Please help me.

thanks and regards

---

### Post by mike1234 on 2008-09-19
> **deepaksinghkushwah said:**
> Hi all, i have a little problem. I hope u all will help me. I have installed ubuntu 10 days ago. that was first time i use it. I was trying to install some software using add/remove program manager in applications. but it was showing the error to use synaptic to install new software. that's why i try to remove synaptic. I use "sudo apt-get remove synaptic" command. but it remove add/remove manger too. now i m unable to use this wizard. is there any option that i can reinstall the add/remove wizard and remove synaptic manager. 

Please help me.

thanks and regards

 Sounds like you have a "big" problem. :) If you "remove" synaptic, how do you plan to install/uninstall software packages?  Just seems weird to me. I like to "see" what I have installed.

M.

---

### Post by Sef on 2008-09-19
> I use "sudo apt-get remove synaptic" commandI don't know if this will work, but try from the terminal this code:

(ether copy/paste or type it in)

```
sudo apt-get update && sudo apt-get install synaptic
```Add/Remove, which is part of Synaptic, is simply a simpler version of Synaptic.  Thus when you uninstalled Synaptic, you uninstalled Add/Remove.

---

### Post by iaculallad on 2008-09-19
> **mike1234 said:**
> Sounds like you have a "big" problem. :) If you "remove" synaptic, how do you plan to install/uninstall software packages? 

M.

By using the terminal:

```
sudo apt-get install synaptic
```

------------------------------------------------

```
apt-cache search synaptic
apt-cache policy synaptic
```

---

### Post by deepaksinghkushwah on 2008-09-19
yet i m using apt-get install command to install the packages :)

---

### Post by deepaksinghkushwah on 2008-09-19
but i want to install again the add/remove wizard

---

### Post by iaculallad on 2008-09-19
> **deepaksinghkushwah said:**
> but i want to install again the add/remove wizard

Try using alacarte to bring the Add/Remove menu back.

```
gksudo alacarte
```

---

### Post by Sef on 2008-09-19
> Try using alacarte to bring the Add/Remove menu back.Easier is System > Preferences > Main Menu  

Alacart has been renamed Main Menu > Applications > check the box next to Add/Remove.  It should be at the bottom.  If not, then use the command in post 7.

---

### Post by deepaksinghkushwah on 2008-09-19
> **Sef said:**
> Easier is System > Preferences > Main Menu  

Alacart has been renamed Main Menu > Applications > check the box next to Add/Remove.  It should be at the bottom.  If not, then use the command in post 7.

there is no option of Add Remove in Main Menu > Application > Addremove

---

### Post by iaculallad on 2008-09-19
> **deepaksinghkushwah said:**
> there is no option of Add Remove in Main Menu > Application > Addremove

That should be: System > Preferences > Main Menu

---

### Post by deepaksinghkushwah on 2008-09-19
main menu is available but Add/Remove is not there. But thanks you all for you kind replies and help.

---

### Post by Partyboi2 on 2008-09-19
> **deepaksinghkushwah said:**
> main menu is available but Add/Remove is not there. But thanks you all for you kind replies and help.
When you removed synaptic you probably removed the gnome-app-install package, so try reinstalling it from a terminal
```
sudo apt-get install  gnome-app-install
```

---

