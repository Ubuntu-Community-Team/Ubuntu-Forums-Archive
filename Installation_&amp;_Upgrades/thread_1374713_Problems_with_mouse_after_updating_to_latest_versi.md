---
title: "Problems with mouse after updating to latest version using apt-get"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by Cozin on 2010-01-07
Hi!

First of all i would like to say that im really new at Linux systems and have never worked with Ubuntu before but decided i would give it a try.

After upgrading to the latest version using a pop-up in gnome i get an error screen when the gui starts. It says:

Ubuntu is running in a low-graphics mode

The followind error was encountered. You may need to update your configuration to solve this.

(EE) Logitech USB-PS/2 Optical Mouse: Read Error: No such device
(EE) Logitech USB-PS/2 Optical Mouse: Read Error: No such device


When pressing OK i get a couple of choices where i can view logs or go to console.

I have tried unplugging my Logitech mouse and use another but that doesn't change the error message.

How do I update my configuration to solve the error?

Thanks

---

### Post by tommcd on 2010-01-07
So you had been running Ubuntu 9.04, and you did an upgrade to Ubuntu 9.10? Is that correct? How exactly did you do the upgrade? Was it like this?
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
Are you able to get to the desktop at all? Or do you just get a terminal prompt? What graphics card does your computer have?

In any case, you could try booting to recovery mode and running:
```
dpkg-reconfigure console-setup
```
Then reboot.
To boot to recovery mode, simply select the recovery mode option from the grub menu when the system boots up. If you do not see the grub menu when you boot then hit the **Esc** key as the system boots to see the grub menu.
If you still can't get to the desktop, them boot to recovery mode and choose the options that says "**xfix fix the video**" (or whatever it says exactly). Then reboot again. If you get errors, note them and post them here if you can. 
Hope this helps.

And welcome to the Ubuntu forums!

---

### Post by Cozin on 2010-01-11
Yes i upgraded from 9.04 to 9.10 using the upgrader you posted a link to.

Since im extremely new at this i didn't know the command: startx

And when i tried typing that at the prompt i got into gnome.

Havn't tried restarting since because the computer is at work so I don't know if the problem still exist. Will try later:)

Thanks for the help.

---

