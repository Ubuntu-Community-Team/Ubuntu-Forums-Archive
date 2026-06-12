---
title: "Unbelievable! xubuntu-desktop became ubuntu-desktop ..."
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by pcit on 2008-07-03
Hi,

Tonight there were a very weird situation. Originally, I installed ubuntu 8.04 server edition to my dell dimension 8400. It worked perfectly, then I decided to install an x environment in case I need to remote login into some other machines and bring up some GUI windows. I chose to install xubuntu-desktop package with "sudo aptitude install xubuntu-desktop" command. 

However, the odd behavior happened after I finished installing the xubuntu-desktop. I executed "startx", then linux start "GNOM DESKTOP"!? How is that possible? I double checked the command I typed and I was sure I didn't put "install ubuntu-desktop"...

Did I mis-typing something? I couldn't understand how the xubuntu became ubuntu ...

Patrick :confused:

---

### Post by pcit on 2008-07-03
[Updated]
After reboot the computer, I saw xUbuntu loading bar(Don't know how to call it exactly...) and the login window is typical xUbuntu theme, too. Though, I got GNOME desktop again after logan...

---

### Post by ibutho on 2008-07-03
If GNOME desktop is indeed installed and you don't need it, you can uninstall it by doing
```
sudo aptitude remove ubuntu-desktop
```

---

### Post by pcit on 2008-07-03
Thanks for the reply:) but the command won't work since I was installing with "xUbuntu-desktop" package. 

Though, I tried the command remove "ubuntu-desktop" command just to see if the GNOME desktop would go away. Usually, I thought if the package *has not* been installed, you would get the error message "the package has not been installed, since it will not be removed" (or something similar) This time, it didn't prompt for this kind of error message!?

---

