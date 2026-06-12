---
title: "Loading terminal instead of GUI"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by vigneshravi on 2006-06-02
Hi. I am new to ubuntu and installed ubuntu on a toshiba protege tablet PC. Since the tablet pc did not have a floppy disk drive or a CD drive. I used a program called instulux which helped me install ubuntu through the net. after going through the installation process and loading ubuntu, i get a terminal instead of a GUI. 
It asks for my login and password. After typing it in, i get the folllowing:
loginName@ubuntu:~$

How do i access the GUI? Thanks a lot!

---

### Post by johnc4510 on 2006-06-02
Do you remember if you install the server version or the full version?

---

### Post by vigneshravi on 2006-06-02
Where did I ahave to make this choice? I dont remember installing the server version anywhere. thanks.

---

### Post by johnc4510 on 2006-06-02
Well, try this:
sudo apt-get install ubuntu-desktop
Put that in after:loginName@ubuntu:~$

---

### Post by vigneshravi on 2006-06-02
I tried that and i got the following error message:
Reading package lists... Done
Building dependancy tree... Done
W: Couldnt stat source package list [http://sg/archive.ubuntu.com](http://sg/archive.ubuntu.com)... -stat(2 No shuch file or directory)

---

### Post by johnc4510 on 2006-06-02
Try:
startx

---

### Post by vigneshravi on 2006-06-02
i tried that and the following appeared:
-bash: startx: command not found

Do you think there was a problem with my installation and i need to reinstall?

---

### Post by johnc4510 on 2006-06-02
I would say so, but you do get to the command line. Let me search for about 5 minutes, then I'll come back.

---

### Post by johnc4510 on 2006-06-02
Try this:
sudo apt-get install x-window-system-core xserver-xorg gnome-desktop-environment

---

### Post by vigneshravi on 2006-06-02
It gives the same error as before. 
Reading package lists... Done
Building dependancy tree... Done
W: Couldnt stat source package list [http://sg/archive.ubuntu.com](http://sg/archive.ubuntu.com)... -stat(2 No such file or directory)

---

### Post by johnc4510 on 2006-06-02
Sorry, I don't think I can help you.

---

### Post by vigneshravi on 2006-06-02
when i press enter it also says E: x-couldnt find package x windows core

---

### Post by vigneshravi on 2006-06-02
do u think u can tell me how i can reinstall the operating system?

---

### Post by jobezone on 2006-06-02
[QUOTE=vigneshravi]Hi. I am new to ubuntu and installed ubuntu on a toshiba protege tablet PC. Since the tablet pc did not have a floppy disk drive or a CD drive. I used a program called instulux which helped me install ubuntu through the net. after going through the installation process and loading ubuntu, i get a terminal instead of a GUI. 
It asks for my login and password. After typing it in, i get the folllowing:
loginName@ubuntu:~$

How do i access the GUI? Thanks a lot![/QUOTE]

Did you download ubuntu regular version or the ubuntu-server version. Ubuntu installs a gui by default, and if it can't, it tells you about it. Since you've arrived at a text login, it could only mean you're using the ubuntu-server.

Nevertheless, I saw the error message you gave, and there's typo in your repositories in /etc/apt/sources.list .
Do:
```
sudo nano /etc/apt/sources.list
```
This will open a text editor with many urls in it. Change the text [http://sg/archive.ubuntu.com](http://sg/archive.ubuntu.com) to the correct [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) 
Then do:
```
sudo apt-get update
```
```
sudo apt-get install ubuntu-desktop
```.

But I still think you got ubuntu-server...:/

---

### Post by vigneshravi on 2006-06-02
When I type in "sudo nano /etc/apt/sources.list"
it says "sudo: nano: command not found"
is there anyway i can install ubuntu desktop now if i have installed ubuntu server?

---

### Post by jobezone on 2006-06-02
Yes, you should be able to the meta-package "ubuntu-desktop", but you seem to have a typo in your /etc/apt/sources.list . That's why I said for you to launch a text editor and correct it. Your system doesn't seem to have nano, either. You may have another text editor, like vi, but you'll find it a bit confusing to use.

Is it too much trouble for you to re-install ubuntu, **but** making sure you get the regular version?

---

