---
title: "X won't start after upgrade to gutsy"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by stubblyhead on 2007-11-13
I recently upgraded to gutsy gibbon on my Dell Inspiron 5100 laptop.  Since then, I have not been able to get X started.  I can get to a prompt in recover mode successfully.  /var/lgo/Xorg.0.log suggests that my hsync and/or my vrefresh is out of whack.  From /etc/X11/xorg.conf, I can see that my hsync range is 31.5-58.5, and my vrefresh range is 49.0-75.0.  What info I could find on dell's support site and elsewhere on the internet suggest that these should be acceptable values for my hardware.  Is there some other change I need to make?  Am I barking up the wrong tree entirely?  Please let me know if more info is required and I will do my best to provide it.  Thanks in advance.

---

### Post by K.Mandla on 2007-11-14
Does the 5100 use an Nvidia card? Is it possible that the newer driver is somehow playing havoc with the card? Nvidia abandoned some older cards between Edgy and Feisty, and my first worry is that it might have happened again with Gutsy. Don't know, though. ...

---

### Post by dustman on 2007-11-14
same problem here. after the reboot that came along with the gutsy upgrade, i get to the login screen...when i input the username and password, the font is huge! (i guess something around 50-60)...after introducing the username and password, i get a blue screen of death (remember msft ;) ) and nothing happens. the only thing i can do is to ctrl+alt+backspace and get back to the login screen, or to ctrl+alt+f1 and get to the terminal. now i tried to ```
dpkg-reconfigure xserver-xorg
``` cause i saw that some were saying this solved their similar problems, but i get:```
/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed
```

i have a toshiba satellite a100-529 laptop, with an ATI xpress 200M graphics card.

---

### Post by stubblyhead on 2007-11-14
> **K.Mandla said:**
> Does the 5100 use an Nvidia card? Is it possible that the newer driver is somehow playing havoc with the card? Nvidia abandoned some older cards between Edgy and Feisty, and my first worry is that it might have happened again with Gutsy. Don't know, though. ...

I don't have access to the machine right now, but I believe it has a Radeon card.  I can confirm when I get home this evening, but I'm fairly certain it is not an Nvidia.

edit:  I confirmed that it is a Radeon Mobility 7500.  Or so claims xorg.conf.

---

### Post by stubblyhead on 2007-11-19
> **stubblyhead said:**
> I don't have access to the machine right now, but I believe it has a Radeon card.  I can confirm when I get home this evening, but I'm fairly certain it is not an Nvidia.

edit:  I confirmed that it is a Radeon Mobility 7500.  Or so claims xorg.conf.

Does anyone have any ideas on this?  I would really like to be able to use my laptop again.

---

