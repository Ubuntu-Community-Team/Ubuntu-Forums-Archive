---
title: "problem in dual boot installation"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by sauravsaha on 2010-09-13
I have a laptop with window 7. i have installed ubuntu with wubi but while installation, i did not get option for root password. i have installed the ubuntu without root password. so i am not able access the root directories. I have wifi office and my laptop is not able to get the wifi network. i have checked the network parameters and they seem to ok. please guide me for right installation of ubuntu as i am a newbie to linux.

---

### Post by Elfy on 2010-09-13
There is no root password.

Use sudo

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by garvinrick4 on 2010-09-13
If you want to use your Desktop (GUI) j then go ALT/F2 and then type in gksudo nautilus

You are now root and what ever you change and save is what you get.
Your password was the one you typed in at install right after it asked you for your name.
At terminal you have to use sudo then a command and it will ask for your password.

```
sudo apt-get update && sudo apt-get upgrade
```

test it to show you when you type your password it will not show you the letters.

---

