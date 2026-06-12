---
title: "No longer able to to switch users"
date: 2019-02-08
forum: Installation &amp; Upgrades
---

### Post by blown2bytes on 2019-02-08
I upgraded from 16.04 to 18.04, but now, I can no longer switch users. It worked before, and I'm still able to login as any of the users, but switching from one to another without logging out doesn't work. At the system menu (gear in the top-right corner of the screen) I can click "Switch User" and it does nothing. Other users show in the menu and I can click them, but that also does nothing (literally nothing... no error or even a single action that I can tell). 


If I hit CTRL+ALT+F1 I get the normal login screen and then can log in as a different user without having to log the previous user out first, but it would be nice for the built-in "switch user" functionality to work like it did before I upgraded. 

I'm using the "Unity" desktop rather than Wayland because there's other glitches occurring with Wayland that cause us not to be able to use it.

Any idea where to look?

---

### Post by deadflowr on 2019-02-09
Switch to lightdm
If the login screen is at tty1 (ctrl alt f1) then you're using gdm.
I think there are some switching issues with gdm.
Lightdm was what Ubuntu used prior to the new desktop paradigm.
And unity works far better with lightdm, anyway. 
lightdm's session screen is at tty7 or (ctrl alt f7, fwiw)

Since this is an upgrade it (lightdm) should still be installed, so it would just be a matter of re-configuring which to set as the system default.
Simple enough with
```
sudo dpkg-reconfigure lightdm
```
then select lightdm from the list and select Ok.
It should apply on a restart/reboot.

If it's bugs out too, try removing and reinstalling lightdm:
[https://askubuntu.com/questions/1044779/unable-to-switch-users-at-lock-screen-unity-ubuntu-18-04]("https://askubuntu.com/questions/1044779/unable-to-switch-users-at-lock-screen-unity-ubuntu-18-04")

---

### Post by blown2bytes on 2019-02-09
Does lightdm work with wayland? I wonder if that would fix our issues using wayland?

---

### Post by blown2bytes on 2019-02-09
Well, that worked... mostly. I'm able to switch users without going to tty1, but the exception is that from the unity desktop I can click on one of the other users in the system menu to go back to the login page (greeter) with that users selected, put in the password, and then login. So that works. What *Doesn't* work, is clicking "Lock User/Switch Account". It just locks the screen and doesn't give me the option to pick a different user (the only user in the greeter list that shows up is the logged in user). In addition, if another user is logged in, it gives an "Authentication Failed" error message and the password field says "Go to greeter". If you click that button it takes you back to the main greeter where all other users are also listed.

When using the "Ubuntu" desktop instead of "Unity" there are 2 separate buttons for logging out and switching users. Switching users from the Unbunt/Wayland desktop takes me back to the normal login page (which I think is normal). 

I'm going to run with the Ubuntu desktop for a while and see if that works better now.

---

### Post by #&amp;thj^% on 2019-02-09
> **blown2bytes said:**
> Does lightdm work with wayland? I wonder if that would fix our issues using wayland?

The Wayland windowing system is not yet fully supported.(MHO) Wayland sessions are listed, but ....
I don&#8217;t think that the use of LightDM instead of native GDM is a good choice for gnome edition.
Lightdm works well with Unity though.

My mileage went like this, I think it defaults to Wayland when using GDM, but it defaults to Xorg when using LightDM. (Loosely speaking)

---

