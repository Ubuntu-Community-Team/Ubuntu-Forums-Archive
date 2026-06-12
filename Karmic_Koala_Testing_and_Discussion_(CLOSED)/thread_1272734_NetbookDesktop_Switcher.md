---
title: "Netbook/Desktop Switcher"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by prattmd on 2009-09-22
I am having all kinds of trouble with the UNR/Classic Desktop switcher.  The initial switch to the classic desktop works great, but then, when I switch back, the gnome classic menu bars at the top and bottom of the screen won't go away.

Even with a restart/boot this does not get fixed...

Any ideas?

---

### Post by GOROSSI on 2009-10-15
Im having the same issue creating a new user account fixed it so its probably a gconf issue.

I broke mine again today & dont want to create a new account again so I will try fix it another way 

I will then get back to you :-) if i do 

else otherwise I will have just created a new user account & copied my files over

---

### Post by xfalcox on 2009-10-15
Got the same **** here, to fix i've deleted 3 folders (.gnome and two others) and after reboot it worked, but i've lost many configurations...

---

### Post by NE Key on 2009-10-15
On Jaunty NBR - when I switched from NBR to classic desktop the menu bars never appeared (killing maximus seems to fix it)

Now on Karmic NBR - when I switch from classic to NBR desktop the menu bars won't go away.

Same problem as you and no idea how to fix it. (Sorry - this must count as a fairly useless post.)

---

### Post by GOROSSI on 2009-10-15
hmm yes its annoying I created a new account again in the end just copied my docs into the public folder & transfered them over.

I would have delete some config folders myself but I didnt have time too I didnt have a quick look in gconf editor but couldnt see anything only how to get the window borders back by disabling maximus

---

### Post by GeorgeVita on 2009-10-15
Hi, are you sure that this 'desktop switcher' will exist in final UNR 9.10 version?

I tried to test it with a daily-live 2 days ago and there wasn't any icon to System Preferences!
> ubuntu@ubuntu:~$ sudo aptitude show desktop-switcher
Package: desktop-switcher
State: not installed
Version: 0.5.8-0ubuntu2
Priority: optional
Section: gnome
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 852k
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.3.6-6~), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>=
         2.2.1), libgconf2-4 (>= 2.23.2), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.12.0), libpango1.0-0 (>= 1.14.0),
         ubuntu-netbook-remix
Suggests: gnome-panel, maximus, netbook-launcher
Description: Switch between desktop modes
 desktop-switcher allows the user to switch between two desktop modes. It currently supports switching between Ubuntu Netbook
 Remix mode and "Classic Ubuntu" (two panels, gnome-like) mode.

ubuntu@ubuntu:~$ desktop-switcher
The program 'desktop-switcher' is currently not installed.  You can install it by typing:
sudo apt-get install desktop-switcher
desktop-switcher: command not found


Regards,
George

---

### Post by GOROSSI on 2009-10-15
I think that maybe an issue with the netbook launcher more than anything else

to access synaptic & the update manager I had to open the menu editor & hide some not esstial stuff such as accibility as I dont need it & the system testing app run I had ran it 

then I could see the hidden apps

I will probably try the daily's just out of curiosity myself but its my birthday this weekend so probably be out LOL

---

