---
title: "Set default OS in Multiboot"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by franklin.vp on 2007-12-31
Hi, 
 I instaled Windows Vista and Kubuntu in my laptop. 
 Everything works well but i want to put Windows Vista as the first item in the menu of grub so it becomes in the default choice at startup.
I think I can't do it from Windows because it doesn't even notice that there is a second operating system instaled. 
I dont know how to do it from Kubuntu. 
Thanks

---

### Post by DirtDawg on 2007-12-31
Install startup manager:
```
sudo apt-get install startupmanager
```
Next, start it with System>Administration>Startup- Manager. Change "Default Operating System" to Windows. 

That should do it. Use caution if you decide to play with other settings.

---

### Post by forestpixie on 2007-12-31
or you could edit the menu to have vista as the default - if you want to do that post back

---

