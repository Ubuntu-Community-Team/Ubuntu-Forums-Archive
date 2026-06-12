---
title: "Ubuntu wont fully start or shutdown"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by whatthefunk on 2010-12-09
I finally got Ubuntu to run on my laptop. However, I can only get it to run in safe mode. When I turn it on, it goes to the login screen. I select my username, type in my password and press login. Then it either goes back to the login screen after thinking for a while or just gives me the background image. If I select to login in safe mode, I can get to the desktop and everything works fine from there, although in safe mode.
 
Then, when I try to shutdown, it closes everything up and goes black, but doesnt actually turn off. The Caps Lock light blinks.
 
Is there any way to fix this? Could it be because my laptop doesnt quite meet the system recommendations? Thanks.

---

### Post by sikander3786 on 2010-12-09
Please post your hardware specs including RAM, processor and graphics card.

Regarding the safe graphics issue:

Press Ctrl + Alt + F1 at your login screen. Log in using your credentials and do these commmands.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

It might throw an error like file not found. Ignore and proceed to the next one.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot!

```
sudo shutdown -r now
```

Try to login normally.

Not sure about shutdown issue though.

---

### Post by whatthefunk on 2010-12-09
256 RAM, Pentium III.  Graphics card...no idea.
 
When I went through the commands you gave me and rebooted, I got to the login screen, logged in and was then directed back to the login screen
 
Is this possibly a graphics card issue?

---

### Post by sikander3786 on 2010-12-10
256 MB RAM and P-III I suspect are too low for regular Ubuntu.

Better go for a light-weight variant, Lubuntu.

[http://lubuntu.org](http://lubuntu.org)

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

