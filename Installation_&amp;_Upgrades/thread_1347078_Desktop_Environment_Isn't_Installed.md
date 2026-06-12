---
title: "Desktop Environment Isn't Installed"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by Joomla12 on 2009-12-05
I've managed to install US from  USB flash drive but when I boot to it from Grub, it just brings me to a terminal based login screen. I can login and then nothing...It sits there waiting for a command. I'm not sure if GNOME is installed or what it is.

---

### Post by gabo.cr on 2009-12-05
Try this command:

sudo /etc/init.d/gdm start

It will ask for your login password.

---

### Post by Joomla12 on 2009-12-05
What does that do exactly?

---

### Post by gabo.cr on 2009-12-05
I'm sorry, I probably had to explain myself more. #-o

If you have Ubuntu Desktop you should have Gnome installed, if you have Ubuntu Server you will only have a black screen like you have right now.
But if you are sure you have Ubuntu Desktop then Gnome is not starting for some reason.
So, after you get the black screen, you can login and then type the command I posted. That command does this:

**Sudo** = is to get authorization to make changes.
(that is why the system will ask for your password again)

**/etc/init.d/gdm** = Is where Gnome is located.

**start** = Is to get Gnome started.


Let me know if that helped your problem.

---

### Post by Joomla12 on 2009-12-06
Ok thank you. :)

I'm still a bit of a novice when it comes to Terminal commands. I'll post back if this a success.

---

