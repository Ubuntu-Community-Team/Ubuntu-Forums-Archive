---
title: "Can't type anything in terminal when request for sudo password comes up."
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by Mooseeeeey on 2010-12-29
I am trying to install Xchat and in the archives I found this code that is supposed to add the repository, and install it.  The code I used is: 
```
sudo sed -e 's/# deb/deb/g' -e 's/edgy universe/edgy universe multiverse/g' -e 's/edgy-security universe/edgy-security universe multiverse/g' -i.backup /etc/apt/sources.list && sudo apt-get update && sudo apt-get install xchat
```
It seems to work but when terminal asks for sudo password I can't type anything.  I'm new so simplified help would be appreciated.

---

### Post by akand074 on 2010-12-29
Yes you can, nothing shows up when you type though. Just type your password and press enter and it should work (even though no characters will actually come up).

---

### Post by coffeecat on 2010-12-29
> **Mooseeeeey said:**
> when terminal asks for sudo password I can't type anything.  I'm new so simplified help would be appreciated.

That is by design, although it does confuse people new to Linux. When you are prompted for a password in the terminal, just type it in. You will get no visual feedback. Then press enter and it will be accepted, or you will get an error message if you typed wrongly.

---

### Post by Mooseeeeey on 2010-12-29
Thank you! Is there a good guide for learning basics of terminal?

---

### Post by oldos2er on 2010-12-29
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

[http://linuxcommand.org](http://linuxcommand.org)

---

