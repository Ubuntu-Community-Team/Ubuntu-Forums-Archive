---
title: "Kdenlive 0.7.6 installation?"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by LeetNeo on 2010-01-01
Can someone tell me how to install Kdenlive 0.7.6? I've extracted it from tar.bz2 to my desktop. Can anyone give me any instructions on how to install through the terminal, I'm still new to Linux, so this is why I need help. I also need step by step instructions as I don't know the commands for the terminal. Thanks in advanced.

-LeetNeo.

---

### Post by LeetNeo on 2010-01-01
Can anyone help?

-LeetNeo.

---

### Post by LeetNeo on 2010-01-02
Is anyone going to help me? Please?

-LeetNeo.

---

### Post by Shazaam on 2010-01-02
Try this...
1. Install nautilus-open-terminal (saves time using the terminal)-
```
sudo apt-get install nautilus-open-terminal
```
2. Open the new folder and look for a "Readme" or "Install" file. They should give you an idea as to what additional files (dependencies) you may need to install and the correct compile commands to use. Install them now.
3. Inside the new folder right-click an empty space and choose "Open terminal here".
4. Normally you would enter these three commands in terminal to install (in order)...
```
./configure
```
```
make
```
```
sudo make install
```
Take note of any errors that print out.

---

