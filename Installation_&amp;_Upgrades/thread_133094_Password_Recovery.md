---
title: "Password Recovery"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by YellowHat on 2006-02-19
I forgot my password and can't login. WTF? Doesn't this OS have someway of password recovery or bypass. I haven't even logged in for the first time yet. This blows.

---

### Post by kaamos on 2006-02-19
Please read the first thread you started in the Absolute Beginner Talk

---

### Post by majikstreet on 2006-02-19
when you boot up your computer, and see the grub screen (it says something like press ESC to enter grub menu) press the escape key, ESC.. then choose the newest kernel with the words (recovery mode) next to it.. 

now you are logged into a root shell.. congrats!

now type passwd youruser
replace youruser with your username
then type in your new password
then repeat it.

then it's changed. now type reboot

then it'll reboot, and you can login :D

---

