---
title: "laptop shutdown during upgrade"
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by vs-punn on 2014-08-22
While upgrading online from 13.10 to 14.04 (64 bit), the laptop hanged.
I restarted it, but after that the following is happening:
when I start the laptop, the ubuntu login windows shows up. After the password is entered nothing happens, and he password box remains blank. If I enter the wrong password, it shows You have entered the wrong password.

the top icons show just three buttons: Language, sound and wheel button with option of suspend, restart and shutdown.
It doesnot get connected to the wifi network or wired.(no icon shows up)
What should I do.

---

### Post by ibjsb4 on 2014-08-22
At the login window press:

Ctrl + Alt + F1

Log in, then:
```
sudo apt-get -f install
```
And post the errors using code tags.

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

---

