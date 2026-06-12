---
title: "authentication without password"
date: 2012-10-13
forum: Installation &amp; Upgrades
---

### Post by cmondz on 2012-10-13
hi,
everytime i want to  download a software or just add new programs , the unbuntu software center ask to authenticate  with password, the thing is that i just got this lap top and dont have the password ...how do i fix this?

---

### Post by hydn79 on 2012-10-13
You don't have the root password? You need to get/find it. Because the other option is to run as root user (not recommended) in which case you'll still need the root password.

---

### Post by zombifier25 on 2012-10-13
> **cmondz said:**
> hi,
everytime i want to  download a software or just add new programs , the unbuntu software center ask to authenticate  with password, the thing is that i just got this lap top and dont have the password ...how do i fix this?

Did you install Ubuntu on the laptop or someone else did? If the latter, contact the installer for the password.
If the former, then if you don't have a password you'll need to reset it.

---

### Post by lisati on 2012-10-13
Use the same password that you'd use to log in to the laptop.

---

### Post by cmondz on 2012-10-13
dont have the root password...the thing is that wanna switch to windows 7....but if i can fix this then i  keep ubuntu.

---

### Post by cmondz on 2012-10-13
how do i reset it... i did run the root option and remount the password...is that what you talking about?

---

### Post by lisati on 2012-10-13
Do you use a password when you first turn the computer on? If so, you won't need a "root" password, just use the same password that you use when you turn your computer on.

---

### Post by cmondz on 2012-10-13
no, i did not...no password when start my laptop.

---

### Post by hydn79 on 2012-10-13
Want to switch to Windows 7? Ok, there you go all your problems solved. jk

Try this:
[http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

---

### Post by cmondz on 2012-10-13
so you mean no way to bypass this situation and keep ubuntu running on my laptop...?

---

### Post by westie457 on 2012-10-13
This is probably what you need. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

This is one of many very useful tutorials on this site.

---

### Post by cmondz on 2012-10-13
i did tried this and changed my password with success, but when i go back in ubuntu and click on ubuntu spftware center to install a program, it aasks for authentication again and again, even after i enter my new password, does not work! Am very frustrated right now...been on it for over 4 hrs. what next??

---

### Post by westie457 on 2012-10-13
I,m thinking that even though you can log in your user ID is not part of sudo which could be the problem. Therefore suggest you follow the advice in this link [http://www.liberiangeek.net/2012/04/quickly-add-users-to-groups-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/quickly-add-users-to-groups-in-ubuntu-12-04-precise-pangolin/)

Warning You might have to run this from the recovery environment to allow you to temporarily by-pass the the default security on the system. Be careful what you do here because it is possible to wipe the whole system if you start playing around.

---

