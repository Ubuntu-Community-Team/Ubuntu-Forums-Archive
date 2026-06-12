---
title: "ubuntu installer freezing !"
date: 2015-08-04
forum: Installation &amp; Upgrades
---

### Post by keloa2 on 2015-08-04
Hey
I'm new to ubuntu and I'm trying to install ubuntu as my primary system 
I downloaded the two versions of ubuntu (14.04 LTS) and ubuntu (15.04)
I tried to install the os via usb stick (tried three different sticks) and a dvd
and always the same problem when I chose try ubuntu the system freezes !
So does any one know how to fix it guys ?
Thanks in advance :)

---

### Post by Vladlenin5000 on 2015-08-04
> **keloa2 said:**
> So does any one know how to fix it guys ?

Perhaps, but it mostly likely depends on the hardware.
Post the specs and we'll see :-)

---

### Post by keloa2 on 2015-08-04
> **Vladlenin5000 said:**
> Perhaps, but it mostly likely depends on the hardware.
Post the specs and we'll see :-)
ok
I own alienware m14 
Nvidia GetForce GT750M with 2GB GDDR5
intel Core I7-4710MQ
HDD 1 TB
SSD 256 GB
16 GB Ram
do you need any extra information about the hardware ?

---

### Post by Vladlenin5000 on 2015-08-04
```
Nvidia GetForce GT750M with 2GB GDDR5
```

^^^^
This. 
You need to boot with *nomodeset*. [https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)
-> F6 and select it

---

### Post by keloa2 on 2015-08-04
I'll try and let you know :)

---

### Post by yancek on 2015-08-04
> press enter to boot , 'e' to edit the commands before booting, 'c' for command-line , ESC to return to the previous menu 				

Hit the e key on the keyboard, use the down arrow key on the keyboard to get to the line beginning with the work linux, right arrow key to the end of the line, leave a space and type in nomodeset and boot.

---

### Post by keloa2 on 2015-08-04
> **Vladlenin5000 said:**
> ```
Nvidia GetForce GT750M with 2GB GDDR5
```

^^^^
This. 
You need to boot with *nomodeset*. [https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)
-> F6 and select it
The same problem !
when I select nomodeset and hit try ubuntu the system load then it freezes

---

### Post by keloa2 on 2015-08-04
> **yancek said:**
> Hit the e key on the keyboard, use the down arrow key on the keyboard to get to the line beginning with the work linux, right arrow key to the end of the line, leave a space and type in nomodeset and boot.
I did what you said then the system was searching in the files then I got a message : found no errors , press any key to reboot

---

### Post by keloa2 on 2015-08-04
> **yancek said:**
> Hit the e key on the keyboard, use the down arrow key on the keyboard to get to the line beginning with the work linux, right arrow key to the end of the line, leave a space and type in nomodeset and boot.
I tried it again but not in the end of the line and it worked ! :)
Thanks man

---

### Post by Vladlenin5000 on 2015-08-04
Nice :-)

Now you can test it and/or install. You'll need to repeat the process for your first boot and then, in low resolution/graphics mode, install the recommended proprietary drivers.
The nomodeset (or any other additional option) shouldn't survive a reboot without further user action(s) but if it does you'll need to reverse the changes (delete "nomodeset") in order to have the new drivers properly loaded.

---

### Post by keloa2 on 2015-08-04
> **Vladlenin5000 said:**
> Nice :-)

Now you can test it and/or install. You'll need to repeat the process for your first boot and then, in low resolution/graphics mode, install the recommended proprietary drivers.
The nomodeset (or any other additional option) shouldn't survive a reboot without further user action(s) but if it does you'll need to reverse the changes (delete "nomodeset") in order to have the new drivers properly loaded.
Thank you for your help :)
now I got this error : 
executing 'grub-install /dev/sda' failed. this is a fatal error
(I'm trying to install the system)
:(

---

