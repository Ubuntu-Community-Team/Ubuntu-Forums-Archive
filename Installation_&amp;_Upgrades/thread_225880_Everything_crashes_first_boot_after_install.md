---
title: "Everything crashes first boot after install"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by Mr_ on 2006-07-30
Hey there, after numerous installs using various versions of Ubuntu, Kubuntu and even an attempt with Fedora, and spending an unlogged amount of time reading countless threads on this forum I'm losing the battle to install anything other than windows on this machine.

After succesfull installs, I reboot and enter the graphical logon screen, enter username and pw and proceed to a barrage of application has been forced to close messages

The actual popups says:

The application "Gnome-settings-daemon" has quit unexpededly
The application "Trashapplet" has quit unexpededly
The application "Clockapplet" has quit unexpededly
The application "Mixer_applet" has quit unexpededly
The application "Gnome-volume-manager" has quit unexpededly
The application "Nautilus" has quit unexpededly

and also:

The Panel encountered a problem while loading "OADIID: Gnome_Mixerapplet"
The Panel encountered a problem while loading "OADIID: Gnome_Clockapplet"

That's the furthest I've ever gotton into the boot process, previous to that I'll get one or two error messages and then a black screen or a you have been looged in for less that 10 seconds message.

I'm installing on the following machine

Abit AV8 Motherboard
Nvidia GT 6600
Athlon 64 3000+
160 GB SATA Drive
10 GB IDE Drive
NEC DVD-RW
Matshida DVD

I've tried installing on both the IDE and the SATA drives. After initial problems with gparted, I started using the text based installers on every occasion. I've tried changing Graphics card drivers through /etc/x11/xorg.conf from 'nv' to 'vesa' 
I've also flashed my BIOS in some hope it would be be BIOS related but nothing.

I've attached files that recommnended to be attached.#

Thanks

Lea

---

### Post by zxee on 2006-07-30
I believe the error message your trying to provide is: "your session only lasted 10 seconds..." If that's what it is-it's a desktop file error which can be resolved, but for the moment the easiest way to test that is to get to a shell or commadline > Alt+Ctrl+F1 and then type > sudo addduser (choose a new user name)  After you've successfully done that try to login using the new user name and password.

---

### Post by Mr_ on 2006-07-31
I tried that but I had the same problems as before

Thanks for the response though :)

---

### Post by louieb on 2006-07-31
[FONT=Arial Black]Just finished upgrading to dapper. I don't know if you have more that 1 distro installed. but if you do check (grub.conf/menu.lst) file. the first entry in my conf file pointed a Fendora kernel to my Ubuntu partition. Needless to say the results were exciting. After straighting out the grub.conf file everything seems to be fine. 
 [/FONT]

---

### Post by Mr_ on 2006-08-02
Ok, I've finally managed to install and logon to ubuntu successfully \o/

I ordered a friend some more memory and on the off chance I stuck it in my machine and tried installing ubuntu. It worked.

Not sure how much of a problem the memory was because I've installed windows on this machine in the last few weeks as well.

Anyway, if you come accross this while installing ubuntu and you stumble over this thread, it might be worth bearing in mind. 


Thanks for the help I've had :)

---

