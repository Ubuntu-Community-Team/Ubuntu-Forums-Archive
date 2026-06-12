---
title: "cannot install anything from software centre"
date: 2017-05-17
forum: Installation &amp; Upgrades
---

### Post by animesh87 on 2017-05-17
Hi I am new to Ubuntu, seem to be facing a major problem in installing softwares required to run videos and mp3s. Software centre doesn't give me the option to install softwares rather shows me "use this source" link whenever I try to install particular software. I have gone through the forum to find out solution to my problem but in vain. Tried installing "restricted extras", but failed again and again. Someone please help me asap.

---

### Post by Xian on 2017-05-17
What is the name of the package(s) are you trying to install?

---

### Post by howefield on 2017-05-18
Which version of Ubuntu are you using ?

If you are not afraid of using the terminal to type in commands, open a terminal window and type..

```
sudo apt update
```

you will be asked for your password, enter it, (you won't see it being typed) and press the enter key, Once that has finished type the following..

```
sudo apt-get install ubuntu-restricted-extras
```

whcih should get you playing "videos and mp3s". You may get a licence screen when a fonts package is being installed to which you must agree, use the tab key to highlight the ok button and press enter...

---

