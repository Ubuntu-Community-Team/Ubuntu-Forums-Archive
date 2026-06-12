---
title: "can't install VLC"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by d525sn on 2008-04-26
Can't get media files to work in movie player, so downloaded VLC to the desktop, however when i double click on it it says 

"vlc-0.8.6f-win32.exe" cannot be opened
No application suitable for automatic installation is available for handling this kind of file

Does anyone have any suggestions as to what i could do????

Thank you

---

### Post by tamoneya on 2008-04-26
exe files are for windows and will not work in linux.  The easiest way to install vlc in linux is to launch terminal and type ```
sudo apt-get install vlc
```

---

### Post by Monicker on 2008-04-26
You downloaded the Windows version. You want the linux version.

Install it from System -> Synaptic Package Manager

or from a terminal: sudo apt-get install vlc

---

### Post by d525sn on 2008-04-26
that makes sense, however if i run the suggested through a terminal it says

robin@dermot-reincarnated:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vlc
robin@dermot-reincarnated:~$

i tried to locate it through the system file menu as well but couldn't find it

any suggestions 
thanks

---

### Post by Monicker on 2008-04-26
vlc is in the Multiverse repository, so you need to enable that.

You can do so in Synaptic, or by uncommenting the appropriate lines in /etc/apt/sources.list.

---

