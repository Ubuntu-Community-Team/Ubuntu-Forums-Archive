---
title: "root access"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by chrisclay on 2010-10-01
hi i am very new to linux ubuntu and i am using server headless and as a server it is fine and all my shares are working but i am trying to install twonkymedia server but to do this it seems i need root access and so could someone please advise me on how to install applications in this way sudo does not seem to work on this 
the guide i am using is here "http://blog.tayfundogan.com/2010/06/how-to-install-dlna-server-on-ubuntu.html" are these commands complete or should ad somthing to them to make them work

regards chris

---

### Post by wojox on 2010-10-01
Have a read about [RootSudo]("https://help.ubuntu.com/community/RootSudo") and be careful.

---

### Post by endotherm on 2010-10-01
well, you generally put 'sudo' in front of each command to make it run as root. 
you can use 'sudo -i' to run multiple commands as root without having to use sudo for each command, or you can use su to switch users to root
```

user@Lucid:~$ sudo su 
[sudo] password for user: 
root@Lucid:/home/user# 
root@Lucid:/home/user# whoami
root

```

---

### Post by luvshines on 2010-10-01
You can easily go to root by first setting up root password:
sudo passwd

Then switching user to root:
su

Use the root access with extreme caution else you would soon be posting the troubles that were caused, unintentionally ofcourse, with root login and messy scripts :D

Good luck, though !!

---

