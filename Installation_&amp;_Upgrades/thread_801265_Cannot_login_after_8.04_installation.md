---
title: "Cannot login after 8.04 installation"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by vintendo on 2008-05-20
Hello, I am having a problem with loging into my desktop. I enter my login info and then it takes me back to the login screen I know i am entering the correct username and password.:(  i have uninstalled and reinstalled 8.04 numerous times and each time changing my login info, still to no prevail. I have no clue how what to do :confused:

---

### Post by jtrindle on 2008-05-20
Try

Ctl-Alt-F1

Which should bring you to a text screen login prompt.  If your user name and password work there, it means that the keyboard layout for Xorg is screwed up.  I think the command to run the configuration again is:

sudo dpkg-reconfigure xserver-xorg


If you can't log in there, it means that your username/password isn't what you think it is.  I'm probably being simplistic here but the user name isn't the first thing you typed in setup ("Full name for the new user") but the second thing ("Select a username for the account").  

Usernames have to start with a lower case letter and can contain only letters and numbers, no punctuation or spaces.  It is probably case sensitive.  The password can be letters, numbers, and punctuation and IS DEFINITELY CASE SENSITIVE.

---

