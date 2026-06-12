---
title: "Dual Boot Default Operating System"
date: 2014-11-23
forum: Installation &amp; Upgrades
---

### Post by rbscairns on 2014-11-23
I have both Windows XP (Home) and Ubuntu 14.04 installed on my PC in a dual boot configeration. When I boot my PC, I am given options on which OS I wish to boot to. The default option is Ubuntu. I want to make Windows XP my default OS.

How can I do this?

---

### Post by mastablasta on 2014-11-24
> **rbscairns said:**
> I have both Windows XP (Home) and Ubuntu 14.04 installed on my PC in a dual boot configeration. When I boot my PC, I am given options on which OS I wish to boot to. The default option is Ubuntu. I want to make Windows XP my default OS.

How can I do this?

easiest way should be to use grub customizer or similar program. or you can do it like this: [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by yancek on 2014-11-24
You need to edit the line below which is in the /etc/default/grub file and replace the zero with the correct number for the menuentry for xp.  You can determine that on boot by looking to see which entry is xp.  Count starts at zero so if xp is the fourth menuentry, change the number to 3.  Open the file with:  sudo gedit /etc/default/grub and after changing save the change and run:  sudo update-grub. 

> GRUB_DEFAULT=0

---

### Post by rbscairns on 2014-11-24
Thank you Yancek. It worked like a charm!

---

### Post by yancek on 2014-11-24
> Thank you Yancek. It worked like a charm! 		

You're welcome.

---

