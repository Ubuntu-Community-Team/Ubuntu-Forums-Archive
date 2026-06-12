---
title: "Terminal wont let me type my password"
date: 2017-01-02
forum: Installation &amp; Upgrades
---

### Post by bob brazie on 2017-01-02
Fresh install of 16.04.1 where I am the only user.
When I type a sudo command it asked for my password. 
When I try to type it in after hitting "enter" it won't let me type anything. Just the white square where I need to start typing my password. It won't let me type anything.
Am am logged in as sudo I believe.
Please, any ideas?
Thanks in advance.

---

### Post by wildmanne39 on 2017-01-02
It does not show your password as you type it, just enter the password then hit enter and if you entered the correct password the command should run, just so you know not all comands show output after they are ran unless the command fails.

---

### Post by deadflowr on 2017-01-02
Unless you set it to show password in your sudoer file the password field is always invisible.
setting  the show password is an advanced feature, not normallly set and one you would need to be familiar with.
Run something like
```
sudo apt-get update
```
then type the password and hit enter and watch the update command run.
if the wrong password is entered you'll get an error.

Don't worry about the cursor not moving.
Since the password field is hidden, it also makes no sense to have to cursor move as doing so might give unwanted eyes a sense of the length it is.
If that makes sense.

semi-ninja'd

---

### Post by bob brazie on 2017-01-02
Thanks to all!

---

