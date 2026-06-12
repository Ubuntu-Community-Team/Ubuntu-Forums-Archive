---
title: "repair ubuntu 10.04"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by aman_d8 on 2010-12-01
[SIZE=3]helllo friends ,
                    i installed windows xp sp2 and then installed ubuntu 10.04.(dual boooted)..due some other reasons i had to reinstall windows ,now i am not able to dual booot with ubuntu ... i don't want to reinstall  ubuntu ,i just need a method to repair ubuntu so that i can again dual boot with ubuntu and windows...[/SIZE]
                  [SIZE=3]thanks in advance ..:)[/SIZE]

---

### Post by cottfcfan on 2010-12-01
Boot into the live CD.
Open a terminal.
Mount the partition that Ubuntu is installed on.
eg. sudo mount /dev/sda1 /mnt (If Ubuntu is on sda1)
then reinstall Grub:
sudo grub-install --root-directory=/mnt/ /dev/sda
This will install Grub, when you boot back into Ubuntu you will need to run.. sudo update-grub
That should do it.

---

### Post by uRock on 2010-12-01
Hello and Welcome to the forums. 

This link will give you in depth explanation of how to reinstall the grub boot loader after installing Windows. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by aman_d8 on 2010-12-01
**[COLOR=black]thanks cottfcfan and urock .... I will try this and let you know ...[/COLOR]**

---

### Post by aman_d8 on 2010-12-29
[SIZE=4]hello  freinds, 
                  I tried the above mentioned method ..but unable to do it properly ....i am attaching the screenshot .....please let me know where is the fault ... [/SIZE]
     
                  [SIZE=4]      thnks in advance ..[/SIZE]:)

---

### Post by cottfcfan on 2010-12-29
I take it your Ubuntu installation is on sda6?
If thats the case then:
```
sudo mount /dev/sda6 /mnt
```
then:
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
Then reboot into your Ubuntu system and run:
```
sudo update-grub
```
That should do it.

ps. the problem is that you`ve tried installing Grub onto sda6, instead of into the root of sda.
The above commands should work.

---

### Post by aman_d8 on 2011-01-02
happy new year to cottfcfan ,uRock,
                                            I tried the method and [SIZE=4]it really worked[/SIZE] ...

[SIZE=4]thanks cottfcfan ....thanks alot 

thanks uRock....thanks a lot ...[/SIZE]



[SIZE=5]may GOD bless you ....[/SIZE] :) :D

---

