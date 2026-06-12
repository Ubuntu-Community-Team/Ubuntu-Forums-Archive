---
title: "Error at install screen with gutsy"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by kenha37 on 2008-04-06
Hi, I&#8217;ve been trying to instal gutsy on my computer for a while now but I haven&#8217;t been able to solve a ata3, something something error... I found that if I wrote irqpoll at first when I have to choose whether I want to install or check for errors on the cd and so on, I am able to surpass this, and know my problem comes: I&#8217;m only able to press f6 when I install feisty, when I try installing gutsy I get this square in the upper left corner where it says something I have no idea what means...

By the way, I am trying to install Linux MCE in this particulary image but its the same if i try using the Ubuntu and Kubuntu Live Cd and also the alternative...

---

### Post by Partyboi2 on 2008-04-08
Have you tried installing with the [alternate cd]("http://releases.ubuntu.com/7.10/")? If so are you having the same problem? Also make sure the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") matches

---

### Post by kenha37 on 2008-04-08
> **Partyboi2 said:**
> Have you tried installing with the [alternate cd]("http://releases.ubuntu.com/7.10/")? If so are you having the same problem? Also make sure the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") matches

Yeah i tried all of these, but every time i get the same screen at start up...

Is there maybe another way to write "irqpoll" at start up?

---

### Post by Partyboi2 on 2008-04-08
I have never experienced not being able to press F6 at the ubuntu main menu screen before. What happens when you check the cd for defects? Another way that maybe work  is to install feisty first, then do a [network upgrade]("https://help.ubuntu.com/community/GutsyUpgrades") to gusty. If you do decide to try upgrading to gusty from feisty after it has upgraded it will ask you to restart the system before doing this check your menu.lst ```
gksudo gedit /boot/grub/menu.lst
``` and make sure that irqpoll has been added to:
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=c61e113a-1e75-40cc-8051-bcceeb33acff ro quiet splash[COLOR=Red] irqpoll[/COLOR] If you need to add it then after you have saved the changes in a terminal update grub
```
 sudo update-grub
```
then restart.

---

### Post by kenha37 on 2008-04-09
Yeah tried checking for defects and i also burned a new one, i even downloaded it one more time and still no change...

I also tried installing fiesty, but when i complete the install it doesn't create the mdadm.conf file... and then i am kind of busted because im not very good at reparing a computer that doesn't work... usually i just format the entire harddrive :p but this isn't quite the solution this time...

---

### Post by Partyboi2 on 2008-04-09
What speed are you burning the iso at? I would suggest trying at a low speed like x4 or less if you havent already done so, as to avoid corruption.

---

### Post by kenha37 on 2008-04-11
> **Partyboi2 said:**
> What speed are you burning the iso at? I would suggest trying at a low speed like x4 or less if you havent already done so, as to avoid corruption.

I just tried this but it doesn't seem to solve the problem :(

Is it maybe possible to change the boot configuration another place than by pressing f6??

---

### Post by Partyboi2 on 2008-04-11
> Is it maybe possible to change the boot configuration another place than by pressing f6?? Not for your situation I don't think there is. Maybe someone else could confirm that.
> 
I also tried installing fiesty, but when i complete the install it doesn't create the mdadm.conf file... and then i am kind of busted because im not very good at reparing a computer that doesn't work... usually i just format the entire harddrive :razz: but this isn't quite the solution this time...      Are you installing feisty from the live cd or alternate cd? The [alternate cd ]("http://au.releases.ubuntu.com/7.04/")is the one  to use if you are trying to set up raid.

---

