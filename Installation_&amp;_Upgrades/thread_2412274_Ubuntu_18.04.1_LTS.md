---
title: "Ubuntu 18.04.1 LTS"
date: 2019-02-10
forum: Installation &amp; Upgrades
---

### Post by QKC on 2019-02-10
I have just bought a new OEM sets. In it is 8700K processor and Z390 Gaming Plus board with Asus GTX1060 6GB graphic card. When I install Ubuntu 18.04.1 LTS, after finishing installing and reboot it will load and then next it will appear user "name" then asking for password. I key in my password but it will say it is not recognized and keep asking for my password. And I cannot use it.

Appreciate if anyone can help to solve the problem cos I have tried reinstalling the OS but still the same problem exist.

---

### Post by ajgreeny on 2019-02-10
What exactly do you mean by "a new OEM sets"?

Was it pre-installed Ubuntu on a new computer?  If so, it will presumably not already have your username and password in the setup, assuming you did not give the retailer that info (dangerous to do!) before taking ownership of the computer.

You may need to add your username and the password you wish to use in those boxes, but I have never seen an OEM install of Ubuntu so you may need to await further responses.

---

### Post by yancek on 2019-02-10
I have no idea either what "OEM sets" refers to so a brief explanation of what you mean might help.  You do state "When I install Ubuntu 18.04.1 LTS" so that means you did the installation.  I've never known of an Ubuntu release that did not require the user installing to create at least one user and one password.  Are you saying you did do that and the user and password fail?  Do you have more than one user?  Are you selecting the correct one?

---

### Post by QKC on 2019-02-10
No what I mean by OEM is it is a customize built by different components. I did the OS installation myself.

---

### Post by QKC on 2019-02-10
I mean it is a customize built by different components. I did the OS installation myself. During the installation I create the user with password and tick "Log in automatically" but after the reboot the system will start up and it will appear user "xxx", password "xxxx". After I key in the password, error appear "password is wrong" and I could not go into the system.

---

### Post by ajgreeny on 2019-02-11
You must be typing something wrongly I suspect but have a look at [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) and you should be able to reset the password that is currently giving the problem.

Make sure to do exactly what is suggested; missing any small action from this will result in failure.

---

### Post by jdeca57 on 2019-02-11
Also, consider your keyboard settings. It is possible that the keyboard you use is not the keyboard that came with the installation. In my region that's qwerty vs azerty but other problems like a caps lock may also be a cause.

---

### Post by QKC on 2019-02-24
Hi
I have done the installation again but I still have the issue. I attach the error picture in it.

---

### Post by oldfred on 2019-02-24
If an OEM install, you first add a user & password once you get system from OEM.
So did you create a user & password?
Why OEM install and not just standard desktop?

       OEM mode so user can add name & password later:
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
[http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install](http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install)
Perform end-user configuration after initial OEM installation 
 sudo apt-get install oem-config-gtk

---

### Post by mastablasta on 2019-02-25
drop to console (press CTRL+ALT+F1) and try to login there. if it says wrong password there, then you are typing it it in wrong. 

due to possible keyboard issue, change a password to an easy one first. if it works, then change it to a more complex one.

---

