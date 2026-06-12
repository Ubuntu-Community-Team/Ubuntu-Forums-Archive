---
title: "Fontconfig warning"
date: 2012-10-25
forum: Installation &amp; Upgrades
---

### Post by chazdg24 on 2012-10-25
I upgraded from 12.04 to 12.10 with no problem.  I am trying to edit the grub file, but in console I get the following message:

Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated


As a result I see nothing when the editor opens.  Is there a fix for this?  I don't see much information on Google about this.

Thanks for any help!

---

### Post by grahammechanical on 2012-10-25
What command are you running? Does this error stop the command from working?

---

### Post by dino99 on 2012-10-25
if your 12.04 was fully updated before upgrading to 12.10 you should not get that issue as the fontconfig change has been made several months back.

rename or delete .fonts & .fontconfig and reboot

---

### Post by chazdg24 on 2012-10-25
> **grahammechanical said:**
> What command are you running? Does this error stop the command from working?
gksu gedit /etc/default/grub

Thanks

---

### Post by chazdg24 on 2012-10-25
Now it works, very strange.  I will report back if it occurs again.

---

### Post by rrnbtter on 2013-02-05
Greetings,
sudo  mkdir .config/fontconfig

sudo mv .fonts.conf .config/fontconfig/fonts.conf

---

