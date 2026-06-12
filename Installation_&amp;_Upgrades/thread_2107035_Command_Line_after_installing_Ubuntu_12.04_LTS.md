---
title: "Command Line after installing Ubuntu 12.04 LTS"
date: 2013-01-20
forum: Installation &amp; Upgrades
---

### Post by shawnstoebe09 on 2013-01-20
So after I install Ubuntu 12.04 LTS on my desktop.. I plug in my Nvidia Geforce 640 2GB DDR3 Asus video card it acts like its gonna boot up. see the purple screen with "Ubuntu" then it goes to the command line and its says login but even if i login it doesn't do anything. Please help I'm very new at this.  Also if I take the video card it works fine. But I wanna be able to play my video games and I see a lot of people have no problem with this card and the version i am trying to use

---

### Post by tgalati4 on 2013-01-21
What happens after you log into the terminal and type:

```
startx
```

---

### Post by dsv47 on 2013-01-21
After you get to the command prompt where it says *login* type your username that you normally login with. Then you will get a prompt to enter your password, and you should type the password that you normally login with. Now that you are logged in type *sudo lightdm* to bring up your normal login screen. You will be asked to confirm this by entering your password. Now you should see your normal login screen, and you will have to enter your password a third time in order to login.

Once you have logged in to your desktop, you can do whatever is necessary to fix your problem so that you can login to Ubuntu normally.

---

