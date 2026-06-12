---
title: "Win 7 Dual Boot Ubuntu 12.10"
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by nj111 on 2012-12-28
Dual Boot Win 7 / Ubuntu 12.10
 
A little of a newbie here guys.
 
After setting it all up and doing the updates, system re-boot, log on screen to put my password in and** incorrect password**.
 
I did not enable the root user - I made sure of that, I created iptables firewall within my Admin/User account.
 
I have tried - recovery - root shell option - Nothing, The system looks like It will boot-up and then goes back to - password_________________
 
Why is my password not working - driving me nuts.
 
HELP - PLEASE???

---

### Post by oldfred on 2012-12-28
Welcome to the forums.

You use sudo for typical root access with Ubuntu by the admin user. Your password is the one you used to create system. It made you type it twice when you installed.

       Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)
[URL="https://help.ubuntu.com/community/WikiGuide"]
[/URL]
[https://help.ubuntu.com/community/WikiGuide](https://help.ubuntu.com/community/WikiGuide)
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by james2b on 2012-12-29
That can caused by a folder and or file ownership and permission issue, back with Ubuntu 11.10 I and others had that type of problem. That can be root ownership of your home folder, or only the .Xauthority file in your home folder, so then it denies permission. So you edit your kernel boot options at the grub boot menu to allow boot to only the run level 3 text console mode, then check or change your home folder and files ownership to your user. Or select your Ubuntu Recovery Mode at the grub boot menu screen, then open a terminal as sudo root to make that change. Here is the forum link with the fix; [http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-cannot-login-and-cannot-shut-down-907558/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-11-10-cannot-login-and-cannot-shut-down-907558/)

---

### Post by nj111 on 2012-12-30
Thank you SO much for your replies and pointers - THANKYOU!!!!!
 
This solved it for me,
 
LQ Newbie
 
Registered: Oct 2011
Posts: 1 
 
Rep: [IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/reputation/reputation_off.gif[/IMG]
 
 
I had the same issue.
There was a .Xauthority file in my home folder owned by root and that prevented me from logging in.
Logging in a text console (Alt+Ctrl+F1 at the login screen) and issuing:
sudo rm ~/.Xauthority
solved the issue.
I hope it helps.

---

