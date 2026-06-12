---
title: "W7+Ubuntu dualboot problems"
date: 2012-09-12
forum: Installation &amp; Upgrades
---

### Post by Feek on 2012-09-12
Hello everyone, 
I'm having some problems installing ubuntu 12.04 in dualboot with windows 7 on Lenovo E330 laptop. I have two discs: 
mSATA SSD (on which I want to install Ubuntu and Windows) and 
HDD for other data. I'm installing from USB stick.

The thing is, I can't get Ubuntu to install properly. 
At first I tried installing the easy way choosing to Install alongside Windows 7, however only the HDD showed in the install location selection list. So I unplugged the physical HDD , then the SSD showed up correctly in the installer. 
The instalation went OK, but after rebooting my PC booted straight to windows (no OS selection during boot). I tried adding the boot entry manually with EasyBCD, but now all I get when selecting Ubuntu on boot is black screen and grub>. Holding shift during boot does nothing.

Any help would be appreciated, thanks.

---

### Post by YannBuntu on 2012-09-12
Hello
Setup your BIOS so that it boots first on your SDD.

---

### Post by Feek on 2012-09-12
Hi, I already did that before the installation.

---

### Post by Feek on 2012-09-12
Alright, so I managed to solve my problem. :D 

The almighty Boot-Repair fixed the problem for me. (ran it as a live-CD)
Still not sure what caused the problems in the first place (obviously grub didn't install right), but the system is now working. :)

---

### Post by YannBuntu on 2012-09-13
> **Feek said:**
> The almighty Boot-Repair fixed the problem for me. (ran it as a live-CD)
Still not sure what caused the problems in the first place (obviously grub didn't install right), but the system is now working. :)

Please indicate your [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") URL (or the URL that appeared after you used the "Recommended repair").
This will give information to understand what was wrong, and what your current situation is.

---

### Post by Feek on 2012-09-13
Yes thanks, here it is:

[http://paste.ubuntu.com/1202285/](http://paste.ubuntu.com/1202285/)

---

### Post by YannBuntu on 2012-09-13
Hello
I see no problem in your current situation.

> **Feek said:**
> At first I tried installing the easy way choosing to Install alongside Windows 7, however only the HDD showed in the install location selection list. So I unplugged the physical HDD , then the SSD showed up correctly in the installer. 
The instalation went OK, but after rebooting my PC booted straight to windows (no OS selection during boot).

I suppose that Ubiquity (the Ubuntu installer) installed GRUB in the wrong MBR. You should report 2 bugs here: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug)

One because Ubiquity couldn't see the SDD if HDD was connected.
The 2nd because Ubiquity didn't install GRUB correctly.

Then please tell us the URLs of the reports so that we can follow-up.

---

### Post by Feek on 2012-09-13
OK, so I tried reporting the bugs using apport: 

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050444](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050444)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050451](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050451)

---

### Post by YannBuntu on 2012-09-13
Good job. Now let's wait the devs answer.

If you have time, please could you suggest translations for Boot-Repair? [https://translations.launchpad.net/boot-repair/trunk/+pots/boot-sav/cs/+translate?show=untranslated](https://translations.launchpad.net/boot-repair/trunk/+pots/boot-sav/cs/+translate?show=untranslated)
Thanks!

---

### Post by Feek on 2012-09-13
Thanks, I'll try to suggest some later. :)

---

