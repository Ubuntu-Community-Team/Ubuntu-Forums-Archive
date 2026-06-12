---
title: "When to update grub.cfg? and how?"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by jagrut911 on 2011-06-27
Dear all,

i am stuck with some silly problem. i have started to port the kernel on my existing system, but somehow i was getting confused.

Actually i have download the latest source code from the [www.kernel.org](www.kernel.org) and started for the further process.

i made untar and put it into /usr/src. 
then i entered into that folder and type the "make menuconfig" command.
then after simply apply the "make" command to compile, and then after apply the "make modules" command.
After completion of this i typed "make modules_install" command.
and finally "make install" command.

Now my question is how to edit and what to edit in "grub.cfg" file.??
And also want to know that if i will apply "sudo update-grub" directly, then what will happen with the image?
Will it be overwrite? and if yes then where and with which file? 
Will it be affected with my next boot?

Please suggest me as soon as possible.

Thanks in advance.

Regards,
Jagrut

---

### Post by Quackers on 2011-06-27
Welcome to UF.
You don't really edit grub.cfg as such, because any edit you make directly will be over-written when grub is updated.
grub.cfg is updated by running the terminal command ```
sudo update-grub
``` in the Linux system which has control of grub. (If you have only one Linux system the last bit is irrelevant).

---

### Post by electron+ on 2011-06-27
hi
update-grub or update-grub2 will be overwrite you grub boot config file and will find all images...

When you run update-grub2 command (if your grub version is 2)
The command will read defaults grub configuration from /etc/default/grub
and will overwrite /boot/grub/grub.conf  file. It will be find all OS's in machine(Linux and Windows).

if your grub version not 2 ,   grub  boot config will be in /boot/grub/menu.lst

Also you can upgrade your grub version runnign this command sudo apt-get install grub-pc

Sorry for my poor English

---

### Post by garvinrick4 on 2011-06-27
> will overwrite /boot/grub/grub.conf  file. 
It is /boot/grub/grub.cfg there is typo.
```
sudo update-grub
```
Above is fine for updating grub:
#grub-legacy (grub) with a menu.lst was last in 9.04 Jaunty version

#Link below will give you all the instructions you need for grub2
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub") 
#This link below is good for installing grub2 (grub-pc) or purging and reinstalling,
Just about instructions on whatever you need to do with your boot loader.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by electron+ on 2011-06-27
> **garvinrick4 said:**
> It is /boot/grub/grub.cfg there is typo.

Sorry  :) yes it is grub.cfg

---

