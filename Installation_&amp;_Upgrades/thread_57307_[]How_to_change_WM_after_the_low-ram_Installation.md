---
title: "[??]How to change WM after the low-ram Installation"
date: 2005-08-16
forum: Installation &amp; Upgrades
---

### Post by Took on 2005-08-16
Hi , every one .

I have never used debian/ubuntu before . A friend told me ubuntu is easy to use and update .So I installed it as the guide-"Mini-RAM HOWTO" which locate at _[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)_ .

The installation was successful (Wow , So easy !) and I got an perfect system then I wanna custom it .

BTW: I use the startx to start the X .**I havent installed the xdm **. 

I used the WindowManager-fluxbox before and the dockapp of it is perfect feature . 

I typed command in my terminal as :
$sudo apt-get install fluxbox 
just like the command in the guide :
$sudo atp-get install icewm 
and all the package was sucessfully installed .

the question is , I dont know how to change my default wm from icewm to fluxbox .

Please notice what I say , **the DEFAULT setting . Not personal setting** such as modify the file: $HOME/.xinirc  . 
(In my home dictionary , there arent .xinirc .xsession and so on )

I dont know where defined the icewm as my default window manager . 

Could you guys please tell me how to do this ?


Thanks a lot !!

Brgs.

Took

..<Sorry for my underprivilege English>..

---

### Post by Took on 2005-08-16
I used some command like this:
$sudo update-alternatives --config x-session-manager

and it echo I only has one window manager to use .

But I have installed the Icewm and fluxbox.

Why ?

Thanks .

Brgs

Took

---

### Post by Took on 2005-08-16
I understand the mean of  update-alternatives .
I used <<$sudo update-alternatives --install x-session-manager x-session-manager /usr/bin/fluxbox 50>> to add the fluxbox .

That's all .

Thanks .

---

