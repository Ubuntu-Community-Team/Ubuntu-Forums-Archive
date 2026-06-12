---
title: "can't &quot;su&quot;? password problem"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by mrbrdo on 2006-07-21
Hello

I just installed Ubuntu 6.06, and i can't "su" in the terminal, because i don't seem to know the password. I don't remember the installation process to ask me for the root password (to set it), only for my user's username and password. Now i don't know my root password, heh. Please help.

regards

---

### Post by PhrankDaChickenGeek on 2006-07-21
Ubuntu uses 'sudo' for root commands. The password is the same as your user password.

---

### Post by tkjacobsen on 2006-07-21
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) discusses the matter

---

### Post by zerwas on 2006-07-21
That's not Ubuntu's philosophy of working with root.

If you want to work permanently with the root-account, do
```
sudo -s
```
Enter the password, you gave on installation, and you are root.
Normally, it should be enough to enter a command with root rights by typing what you want and setting a "sudo" before. :)

Ok, i'm not good in explaining, simply watch [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Greetings,
zerwas

---

### Post by mrbrdo on 2006-07-21
thanks, sudo -s sounds nice.
someone told me how to set the root password (which is not set at start).. i guess you could always use sudo -s, but if anyone needs to set the root password, you have to "sudo passwd root".

thanks all

---

