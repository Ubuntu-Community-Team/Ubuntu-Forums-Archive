---
title: "Trying to switch from ubuntu desktop to netbook remix"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by johnclee on 2010-08-06
Hello I am very new yet interested in opoen source software but am primarily a windows user.  I have an old Dell Inspiron 1000 that I installed Ubuntu desktop version on; now I would like to try the netbook remix as so it will improve the performance of the machine.  I tried to create a start up disc/usb... as the ubuntu website told me but it is not allowing me to I have tried to boot the netbook iso from a disc and the flash drive and have set my boot priority, what am I doing wrong?  thank you for your assistance.

---

### Post by sikander3786 on 2010-08-06
Hi.

Please post few more details. You are not even able to boot from the cd or USB or is there any error message?

---

### Post by kr651129 on 2010-08-06
What motherboard do you have on your laptop, how old is the machine?  And how large is the flash media?

---

### Post by ajgreeny on 2010-08-06
Why not just add **ubuntu-netbook** to what you have already got?
```
sudo apt-get install ubuntu-netbook
``` will do everything for you, then logout, and at the login screen choose the UNR at bottom right where "Desktop" is shown.

The differences in the overall system are not huge, and there is very little point in starting all over again.

In fact, I did the opposite as I already had the UNE iso file for a netbook and on my desktop machine, I installed that and then added **ubuntu-desktop** to get the bits I was missing with the UNE but wanted for the desktop.

Worked brilliantly, and will work the other was just as well.

---

### Post by snowpine on 2010-08-06
You can install the netbook remix on your existing Ubuntu. No need to reinstall. Look for it in the Ubuntu Software Center or:

```
sudo apt-get install ubuntu-netbook
```

Once it's installed, log out, and you can choose the netbook launcher from the Sessions option on the login screen.

It's the same core system with identical system requirements, so it is unlikely you'll see a performance boost (also please note your computer is not technically a "netbook"). Xubuntu is the lighter-weight option if you have old hardware (or you could go with something even lighter like Puppy). :)

More information here: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

