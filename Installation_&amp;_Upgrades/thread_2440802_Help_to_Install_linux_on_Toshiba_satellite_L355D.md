---
title: "Help to Install linux on Toshiba satellite L355D"
date: 2020-04-15
forum: Installation &amp; Upgrades
---

### Post by frank18 on 2020-04-15
[COLOR=#000000][FONT=Verdana]Hi guys hope you ok on this difficult time.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]my son brought me a Laptop Toshiba Satellite L355D Amd Turion 64x2 TLco 2.ghz ,3Ghz ram 32bit with vista installed,but it's sluggish and might have virus and lack of updates,in the end doesn't work right,no updates no assistance from Microsoft.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]i tried to install XUbuntu 18.04 from a CD,it downloads right and after download it starts to install but some time after it goes blank and hangs in there ,it wont install, i restart and it asks for a boot cd , anything that i can do different?thanks.[/FONT][/COLOR]

---

### Post by mörgæs on 2020-04-15
For how long time are you waiting when it pauses?

---

### Post by pcfan1234 on 2020-04-16
Try the Netboot Installer [http://archive.ubuntu.com/ubuntu/dists/eoan/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/eoan/main/installer-amd64/current/images/netboot/mini.iso)
Then select Xubuntu Desktop if you're asked to.
It is 19.10, so you have to upgrade to 20.04 until July.

---

### Post by guiverc on 2020-04-16
If I have an install fail, I go back to what I consider prior steps.

When you downloaded the ISO, did you verify it was perfect?  ([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0))
and then did you verify the write to your install media was likewise flawless ([https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck))

The links were written for standard Ubuntu, but apply equally well to all flavors.  The "*Check disk for defects*" means your install media (CD/DVD/hdd/ssd/thumb-drive/flash-card/other and it's called CD for historical reasons...)

Also if I can't validate the install on the intended install box, I walk the install media to another box and use another box to perform the "*Check disk for defects*" on that box. If it fails on two boxes; I assume that's a fail result.

---

### Post by dragonfly41 on 2020-04-16
[Similar discussion here]("https://www.linuxquestions.org/questions/linux-newbie-8/help-to-install-linux-on-toshiba-satellite-l355d-4175673297/").  32bit or 64bit iso?

---

### Post by frank18 on 2020-04-16
[COLOR=#000000][FONT=verdana]thanks mate this one is 32bit,it fooled me cause i thought this one was 64 ,maybe bios can be updated but not worth it ,i was able to install xubuntu18.04 32bit though and it's running great,thanks[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-04-16
32-bit is a dead-end. Xubuntu 18.04 being a flavor has only 3 years of support so your will end in April 2021. After that no more Ubuntu for you.

Your CPU (and chipset) is 64-bit therefore a 64-bit OS can and should be installed. A 32-bit OS can be installed in 64-bit hardware but just because you can doesn't mean you should. The other way around obviously not possible.

In a nutshell, you should have troubleshooted the 64-bit installer.

---

### Post by frank18 on 2020-04-20
> **CelticWarrior said:**
> 32-bit is a dead-end. Xubuntu 18.04 being a flavor has only 3 years of support so your will end in April 2021. After that no more Ubuntu for you.

Your CPU (and chipset) is 64-bit therefore a 64-bit OS can and should be installed. A 32-bit OS can be installed in 64-bit hardware but just because you can doesn't mean you should. The other way around obviously not possible.

In a nutshell, you should have troubleshooted the 64-bit installer.



Thanks mate; Today i gave another try to Xubuntu 18.04 64 bit and this time i was able to install it,what i did different ,i  i downloaded  distro and did a new CD iso and this time it installed ok

,What do you mean:   Xubuntu 18.04 being a flavor has only 3 years of support so your will end in April 2021. After that no more Ubuntu for you?.
 thanks

---

### Post by yancek on 2020-04-20
> What do you mean:   Xubuntu 18.04 being a flavor has only 3 years of support so your will end in April 2021. 

Support for UBUNTU 18.04 is for 5 years, until April, 2023.  This is the same for some other derivatives of Ubuntu but NOT for Xubuntu.  See their site at the link below.

[https://xubuntu.org/](https://xubuntu.org/)

---

### Post by frank18 on 2020-04-21
> **yancek said:**
> Support for UBUNTU 18.04 is for 5 years, until April, 2023.  This is the same for some other derivatives of Ubuntu but NOT for Xubuntu.  See their site at the link below.

[https://xubuntu.org/](https://xubuntu.org/)


thanks mate.You think the Xubuntu 20.04 wont run on this machine?

---

