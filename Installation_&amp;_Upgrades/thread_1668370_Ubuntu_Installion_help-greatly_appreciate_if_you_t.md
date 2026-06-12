---
title: "Ubuntu Installion help-greatly appreciate if you take a look"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by brobanmanx on 2011-01-16
Can anyone tell me how to install ubuntu 10.4.1 with windows xp pro sp3 so that its a dual-boot? (can choose which one i want to use at boot). Thanks. 
 
 
 
I tried installing with wubi and i kept getting this error message "Exception Processing Message c0000013 Parameters 75b6bf7c 4 75b6bf7c 75b6bf7c" Over and over. Then when it finally dissapeared (As in a kept pressing continue) i decided to cancel it cause i knew something was wrong. Either way the first time i installed it, reboot, nothing really happened. Just booted normally using windows xp.
 
 
Computer specs: Windows Xp pro sp3, Intel core2 duo e6400, 3gb ram, nvidia geforce 7300 le, two 250gb hard drives, asus basswood motherboard. **Doesnt get any worse then this :)**

---

### Post by Rubi1200 on 2011-01-16
Hi and welcome to the forums :)

As far as the failed Wubi install is concerned, it sounds as if either the image was corrupt or you needed to put the wubi.exe file and the downloaded ISO image in the same folder.

For a dual-boot install, see the following links:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Before you start, however, I suggest you do the following:

1. post the specifications for the computer

2. download the ubuntu iso: [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

3. check the integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

4. burn to CD at the lowest speed: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

5. try as a LiveCD first to see that everything works as it should (don't forget to set BIOS to boot from the CD drive first)

6. from the LiveCD, go to Applications > Accessories > Terminal and post the output of the following command so we can check the state of your drive to make sure there is enough space etc. to do what you want
```
sudo parted -l
```(lowercase L not 1)

With all this done, you should be ready for a safe and happy dual-booting experience.

If you have any questions, feel free to ask.

---

### Post by brobanmanx on 2011-01-16
IM having a bit of a problem with the Md5sum integrity thing. Ive done everything it says to do, however when i do what it says in the terminal the terminal just says "The system cannot find the specified path" and "is not recognized as an internal command or external command operable program or batch file" Could you help me out? i have all the files in the specified directy. C:\Documents and Settings\HP_Administrator

---

### Post by Rubi1200 on 2011-01-16
Did you follow the instructions on how to do this in Windows?

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)

---

### Post by brobanmanx on 2011-01-17
Finally got it to work, thanks a ton. However its a little more mac-ish then i thought it would be, but still is pretty nice. Gonna have to get used to hitting the x button on the left side. Up-side is when i get my new comp in a month i dont have to pay 100 dollars for windows. (I dont game on my comp, just on xbox)

---

### Post by Rubi1200 on 2011-01-17
Excellent! Glad you got it sorted out.

No problem for the help and feel free to come here and ask questions at any time.

Enjoy :)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

