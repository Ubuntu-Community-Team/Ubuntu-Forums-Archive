---
title: "Problem at  the installation of Ubuntu 20.04 in my new laptop ASUS TUF GAMING FX506L"
date: 2021-04-13
forum: Installation &amp; Upgrades
---

### Post by josergarcia on 2021-04-13
Hello,
I'm trying to install Ubuntu 20.04 in my new laptop ASUS TUF GAMING FX506L.
The installlation goes with no problem until i download and install actualizations.
When the PC restarts, after quite a while shows: [62.301988] ucsi_acpi usbc000:00:PPM init failed (-110)
Could anyone help`me with this problem? Tank you.

---

### Post by josergarcia on 2021-04-13
The smiley is really colon P. Sorry

---

### Post by CelticWarrior on 2021-04-13
Does it prevent booting?
If not, you can ignore it.

---

### Post by josergarcia on 2021-04-13
I'm afraid that it prevents booting

---

### Post by josergarcia on 2021-04-13
I've tried not using propietary drivers  and to actualice only ubuntu actualizations. Tree times the same message.

---

### Post by CelticWarrior on 2021-04-13
So try the proprietary drivers...
Why would a sane person want a gaming laptop with at a GTX1050, GTX1650 or GTX1660TI and NOT install the Nvidia drivers?

And while there are many reasons to install the latest LTS release, which you did, it's not recommended in this case because most of the hardware, namely the AMD Ryzen 5 or 7 are newer than that release. I suggest the upcoming 21.04 that later can be upgraded to 21.10 and finally 22.04 will be the next LTS.

---

### Post by josergarcia on 2021-04-13
Thank you for your answers. It's no bad idea to try 21.04 and let's see. But processor it's i7 in this laptop, and one of my tries was with propietary. Nothing worked.

---

### Post by CelticWarrior on 2021-04-13
Don't forget to disable Secure Boot.

---

### Post by josergarcia on 2021-04-13
ok

---

### Post by ubfan1 on 2021-04-13
Also check the vendor's site for any firmware updates for your machine.  That may eliminate some problems.

---

### Post by josergarcia on 2021-04-15
I update: The system isn't hanged. if i hit Ctrl+Alt+F2..., opens a terminal session. I introduce user an password and I'm in. The first session remains freezed with the message above: [62.301988] ucsi_acpi usbc000:00:PPM init failed (-110)


 if in the second instance i type: sudo apt-get install --reinstall  ubuntu-desktop, then when i switch to the first instance, there it is  grafic environnment askin for user. I identify and normal ubuntu  desktop. BUT, if now restart the machine appears again: [62.301988] ucsi_acpi  usbc000:00:PPM init failed (-110).


 I've tried to use boot-repair-disk  to repair grub and no, no, no. If you've got any idea to continue will be welcome. Thanks.

---

### Post by josergarcia on 2021-04-15
SOLVED.

I was able to install latests propietary drivers from NVIDIA and the problem seems to be solved.

Thank you for your interest and help.

---

### Post by ubfan1 on 2021-04-15
It is of interest to us which driver you got that worked.  The one in the standard repositories is 460.56 as of a few days ago.  Not sure what version the graphics-drivers PPA is offering.

---

