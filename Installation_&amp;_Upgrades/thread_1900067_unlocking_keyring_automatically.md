---
title: "unlocking keyring automatically"
date: 2011-12-25
forum: Installation &amp; Upgrades
---

### Post by Borunco on 2011-12-25
Hi all, I have been using Lubuntu now for about two months. I have Lubuntu 11.04 installed on my net book over Ubuntu 11.04. My recent problem is that when I would boot up, the keyring would automatically install and my wireless connection would be on. Now for some reason when I boot up the computer asks me for my keyring password, before i can get my connection established. I think but not sure this started happening after I tried a live session of a distro ( don't remember which one). The question is how can I put that keyring on auto again. I have notice that when I do a clean install on my other experimental boxes That some times t
 the keyring password goes on automatically and some times not, I don't know why that is, but would like to learn.
Thank you for the help
Borunco

---

### Post by bobsageek on 2011-12-25
[This topic at AskUbuntu ]("http://askubuntu.com/questions/867/how-can-i-stop-being-prompted-to-unlock-the-default-keyring-on-boot/875#875")covers what you need.

---

### Post by Dennis N on 2011-12-25
This worked for me with Lubuntu 11.04:

Go to edit connections (right click on signal strength bars), select your wireless connection, press the edit button. Check the box at the bottom which says "make connection available to all users" or something close to that. Exit the dialog.

After that, you should not be asked for a password to connect after you log into your account.

---

### Post by Borunco on 2011-12-25
Thank you bobsageek, and Dennis n both methods worked great.:guitar:
Borunco

---

