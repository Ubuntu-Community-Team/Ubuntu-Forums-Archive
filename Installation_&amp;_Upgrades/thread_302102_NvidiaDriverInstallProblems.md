---
title: "NvidiaDriverInstallProblems"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by doh224 on 2006-11-18
hi all.

I am trying to install this file: NVIDIA-Linux-x86-1.0-7664-pkg1.run
I go to the terminal and type sudo sh (thefile.run) and I come to the install . but it say I have a x server running. I have tried to shutdown all running programs but it says that "there seems to be a x server running" ?
what to do? 
thanks for the help, if help comes.
-doh

---

### Post by pay on 2006-11-18
Try this
```
/etc/init.d/xdm stop
```

---

### Post by pay on 2006-11-18
Also look here [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

### Post by bulldog on 2006-11-18
Or just CTRL>>ALT>>F1 to go to a console.

---

### Post by doh224 on 2006-11-18
ok then it says that I don't have such file?

---

### Post by bulldog on 2006-11-18
You have to navigate to the folder where the file is,just like you do in a terminal.
Console is just a big terminal without the GUI.

---

### Post by doh224 on 2006-11-18
> **bulldog said:**
> Or just CTRL>>ALT>>F1 to go to a console.

first: how do I get out of the console again?
and it still says that there are a x server running? 
:confused: 
-doh

---

### Post by bulldog on 2006-11-18
To get back to your GUI CTRL>>ALT>>F7. sorry should have told you.:D

---

### Post by doh224 on 2006-11-18
thats ok :) but why does it still say that there is a x server running?

---

### Post by pay on 2006-11-18
Try Ctrl+Alt+F1 and then ```
/etc/init.d/xdm stop
```to stop the xserver. To start it again do ```
/etc/init.d/xdm start
```ctrl+alt+F7

---

### Post by doh224 on 2006-11-18
> **pay said:**
> Try Ctrl+Alt+F1 and then ```
/etc/init.d/xdm stop
```to stop the xserver. To start it again do ```
/etc/init.d/xdm start
```ctrl+alt+F7

ok.. I've just tried but it says that there is no such file. but I've tried to use the tab, to see what it comes up with: 
/etc/init.d/x11-common 
thats the only file there is. 
shall I stop this file insteed?

---

### Post by pay on 2006-11-18
I'm a Gentoo user so Ubuntu must do things slightly differently. try Ctrl+Alt+Backspace

---

### Post by patrickfromspain on 2006-11-18
Ctrl + Alt + F1

sudo /etc/init.d/gdm stop

cd to the folder where the nvidia instaler is.

sudo ./NVIDIA*.run

after installation is complete:

sudo nano /etc/X11/xorg.conf

and search where it says Driver "nv" or "vesa" and replace it with "nvidia"

Ctrl + O (O as in out, not a zero) to save the file and Ctrl + X to exit nano.

sudo /etc/init.d/gdm start

should be fine.

---

### Post by doh224 on 2006-11-18
:s  ok. but do you think I should stop this insteed? or> 

-doh

---

### Post by doh224 on 2006-11-18
> **patrickfromspain said:**
> Ctrl + Alt + F1

sudo /etc/init.d/gdm stop

cd to the folder where the nvidia instaler is.

sudo ./NVIDIA*.run

after installation is complete:

sudo nano /etc/X11/xorg.conf

and search where it says Driver "nv" or "vesa" and replace it with "nvidia"

Ctrl + O (O as in out, not a zero) to save the file and Ctrl + X to exit nano.

sudo /etc/init.d/gdm start

should be fine.

ok the gdm stop fine. but it still say that there is a x server running? 
and then I say gdm start It says fail?

---

### Post by ububaba on 2006-11-18
> **doh224 said:**
> ok the gdm stop fine. but it still say that there is a x server running? 
and then I say gdm start It says fail?

I updated from Breezy to Dapper. While in the process of installing
the newly updated files through the manager, it froze. After the restart
I simply can't get to the login page. All the attempts at changing the 
contents of *xorg* file have had no effect. I have changed, to nv nvidia, 
vesa but all to no avail! So, I keep going back to  
**[COLOR="Red"]sudo nano /etc/X11/xorg.conf again and again[/COLOR]**. Suggestions please.:confused:

---

### Post by doh224 on 2006-11-19
> **doh224 said:**
> ok the gdm stop fine. but it still say that there is a x server running? 
and then I say gdm start It says fail?

I still have problems with a x server. it still says somethings running?

---

