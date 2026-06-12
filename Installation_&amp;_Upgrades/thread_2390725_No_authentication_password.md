---
title: "No authentication password"
date: 2018-05-01
forum: Installation &amp; Upgrades
---

### Post by evona on 2018-05-01
Dear all,

I have Ubuntu 16.04.4 LTS (Lubuntu) which was installed in a PC repair shop.

When I asked for the authentication password, I was told that I do not need one.
However, I cannot update, install or change anything on my laptop without this password.

I tried to change it by accessing GRUB but my keyboard did not work properly (hitting Ctrl+C and F12 did not help).

I am not very comfortable with the command line. Please, could you provide me with a step-by-step guide how to fix this problem (if it can be fixed)?

Any help in this matter will be greatly appreciated,

Frustrated user

---

### Post by ubfan1 on 2018-05-01
Normally, a user has a login password, and that password is what is used to run commands with sudo as root.  Do you have a user password (it is possible to set things up without)?  Did you try to run your
sudo apt-get update
sudo apt-get dist-upgrade
commands with sudo?
If you give the password, and sudo claims you are not allowed to use sudo, you have to add your user to the /etc/sudoers file.

---

### Post by PaulW2U on 2018-05-02
> **evona said:**
> When I asked for the authentication password, I was told that I do not need one.
However, I cannot update, install or change anything on my laptop without this password.

I tried to change it by accessing GRUB but my keyboard did not work properly (hitting Ctrl+C and F12 did not help).

I can't find the guide that I used last week when I decided to use a different password while testing Ubuntu and then immediately forgot what it was.  :)

Does the guide at [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword) help or have you already tried something like that? It's not too clear how far you got in your attempt to rectify the situation but pressing *SHIFT* while booting up should display the grub menu that you need to access to start the process which will only take you a couple of minutes.

---

### Post by evona on 2018-05-06
Dear PaulW2U,

Thank you for your response. 
I have tried to follow this guide, however, once I am in a "rescue mode" my keyboard does not work. 
I managed to get to root@user, but at this point I cannot type the command. When I am trying to type, the keys do not work or display completely different symbols. 

Regards

---

### Post by evona on 2018-05-06
Dear ubfan1,

Thank you for your response. 
I do not have a login password or any other kid of password. 
I have tried to use the "sudo apt-get update" but then I am asked for the user password. 
When I tried to add a new user in the User settings, it also asked me for the authentication password.

---

### Post by ubfan1 on 2018-05-06
Maybe the lack of a password is confusing things.  Just set a password on your account, and see if that fixes things.  The command to change/set passwords is:
passwd
and you should be able to change it without sudo.
If sudo still doesn't work with a password, complaining about user not in the sudoers file, then that can be fixed by editing the /etc/sudoers file (booting from an install media, mounting the root, and editing the file).  But wait to see if that's even necessary.

---

