---
title: "So new it hurts"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by RejectsRus on 2012-12-29
I`v installed ubuntu (lastest) and at startup it says sumthin about video and safe???? but dont start. i`v tried all the options but nothin.
i know my way around windows to the point every1 i know comes 2 me when windows is actin up but here i`m lost. i dont know where 2 start. 
its a ati 5770 card. ubuntu does start off the disk.
if any1 out there is willin 2 teach me the 101 stuff, thanks..... i really hav no idea and i`m sure teachin me will b like pullin teeth :)
x

---

### Post by Frogs Hair on 2012-12-29
Hello and Welcome

If you are dual booting with Windows knowing the version is helpful. There is documentation available to help with a dual boot. After looking it over you should be able to clarify the problem.  

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by RejectsRus on 2012-12-29
yes its on with 7. it installed without any problems. i just get this message about safe grafixs and thats that. ubuntu just wont start. i get a bunch of options but all of them just goes 2 the command prompt

---

### Post by gnush on 2012-12-29
You're quite ambiguous - can you write down the error message you receive in more detail?

Furthermore, did you experience any similar problems when you tried the live-cd?

---

### Post by grahammechanical on 2012-12-29
May I suggest a few things?

At the boot menu (Grub menu) select Recovery mode. If you are using Ubuntu 12.10 you will find a recovery mode option under the Advanced Options submenu.

From the Recovery mode menu select Resume. That may load a desktop with the default open source video driver called Nouveau.

Once you get to a desktop you can try to activate a proprietary video driver for your video adapter.

In 12.10 go to System Settings in the Power/cog menu and open Software Sources and go to the Additional Drivers tab. You may see 3 versions of proprietary video drivers that you can experiment with.

Another thing to try.

At the Grub boot menu select Ubuntu and press E. That will put you into edit mode. You will see boot parameters for Ubuntu. Look for a line that says

> quiet splash

and change it to

> nomodeset quiet splash

then press F10 to boot Ubuntu. That may get you to a desktop from where you can activate a proprietary video driver.

If you edit the boot parameters to remove "quiet splash" then you will see errors messages when Ubuntu boots that may give clues as to what is going wrong.

In 12.04 you need to look for the Additional Drivers utility (I think. I am not on 12.04 at the moment)

Regards.

---

### Post by RejectsRus on 2012-12-29
quote.... your screen, graphics card, and or input device settings could not be detected correctly. you need to configure these youself.
i get 4 options, all take me to what i know as the command prompt

---

### Post by dino99 on 2012-12-29
sorry, but using nomodeset is really a bad idea, simply remove splash.

---

### Post by dino99 on 2012-12-29
> **RejectsRus said:**
> quote.... your screen, graphics card, and or input device settings could not be detected correctly. you need to configure these youself.
i get 4 options, all take me to what i know as the command prompt

which kind of installation is it ? real or virtual ?

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by RejectsRus on 2012-12-29
im sorry i have no idea what nomodeset and splash mean :(
ps real

---

