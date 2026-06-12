---
title: "x server failed to start( New to ubuntu)"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by foots2015 on 2006-07-04
Hi I am brand new to using linux.

Here is my hardware

celeron d 3.06 ghz. (64 bit)
1 gig ram
nvidia geforce 6200 by pny

Here is my problem and since i am new to ubuntu i don't understand jack about what is going on. 

I have tried to install ubuntu with both the 32 and 64 bit from a disk. When I restart the pc the ubuntu screen comes up and asks me to install. I choose start/install. the next thing that happens is a screen comes up with text (loading restricted drivers ... ok, etc) then I get a screen that says <Failed to start the x server would you like to view the x server output to diagnose the  problem , yes, no.> I choose yes, it gives me a screen with a bunch of text and <Ok> next it says, <would you like to view the detailed x server output as well? , yes, no,>. I choose yes. More text comes up with <ok>. After this a new screen comes up with < x server is now disable. Restart GDM when it is configured correctly , ok, >. After this i get a command line with <ubuntu@ubuntu:~$>.

I have tried both the normal install, and the start in safe graphics mode install.


I don't know what to do can some one please help me?

---

### Post by tseliot on 2006-07-04
1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

If nothing works and the Xserver just crashes, please post the output of the following command:
```
lspci
```

---

### Post by foots2015 on 2006-07-04
i using the live cd and so when it reboots is it going to reset everything?

---

### Post by foots2015 on 2006-07-04
*bump*

---

### Post by foots2015 on 2006-07-04
My main problem is that i need to get ubuntu installed in the first place but i don't' know how to install it from the command line. ( i was hoping to install from the desktop like they advertised). The reason that i need to get ubuntu installed to the hard disk is so i can than restart the computer without reseting the, sudo dpkg-reconfigure xserver-xorg, settings. Is it not true that if you are running off the live cd that when i restart the computer it resets the settings? So i guess what i need is to know how to install ubuntu from the command line.

Ps. I am going to download the alternate version of Dapper Drake, and try it.

---

### Post by tseliot on 2006-07-05
[QUOTE=foots2015]Ps. I am going to download the alternate version of Dapper Drake, and try it.[/QUOTE]
I find the alternate installer easy to use

---

