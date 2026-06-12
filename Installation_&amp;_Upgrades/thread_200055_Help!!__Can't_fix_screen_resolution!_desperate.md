---
title: "Help!!  Can't fix screen resolution! desperate"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by zoon_unit on 2006-06-19
Okay, I managed to get Ubuntu installed by using the text based install, but when I log in, the only screen resolution available is 640x480.  (not too useful)

I have an old Geforce2 MX 400.  I've installed the nvidia-glx-legacy driver and the nividia splash shows up on boot.  My xorg.conf shows the card correctly, shows my monitor as plug and play, and shows all the proper screen resolutions under "Screen" section.

Only problem is, none of them show up in Preferences.  Only 640x480 and 60 hertz refresh.

What am I doing wrong???  This is the only thing holding me back from using the system.  HELP!

---

### Post by Winblowz on 2006-06-19
Have you tried "dpkg-reconfigure xserver-xorg"?

---

### Post by johnc4510 on 2006-06-19
It should be:
sudo dpkg-reconfigure xserver-xorg
Type this in terminal:
For gnome:Applications>Accessories>Terminal

---

### Post by zoon_unit on 2006-06-19
I've got one other question.  I installed Ubuntu desktop so I could get familiar with all of Ubuntu's services, but what I really need is a LAMP installation.

If I install the network Ubuntu, what do I lose from the desktop version?

Can I install LAMP to the desktop, or is this more trouble than it's worth?

Thanks for helping out a LINUX newbie!

---

### Post by Winblowz on 2006-06-19
LAMP is a separate installation option of Ubuntu. It is an option included only in the Ubuntu Server install cd. What you could do (if you want to) is download the Ubuntu Server cd, burn the iso, and boot the option "install LAMP server". Then, when it is all done, do "apt-get install ubuntu-desktop". A gui is not included with the Server install cd, so you could do the quick LAMP server setup, and then install the gui.

---

### Post by zoon_unit on 2006-06-20
Winblowz,

I took your advice and installed the LAMP system, then installed the desktop per your instructions.  But the system still boots up in character based Linux.  How do I invoke (and leave) the desktop??

Thanks for the help.  As you can probably surmise, I'm a total Linux newbie.  Until I learn my way around Linux, I figure the desktop will help out to get things accomplished as I struggle to build a LAMP based website.

Thanks!

---

### Post by rcarring on 2006-06-20
If you are booting to a command line, typing the command "startx" should load the default gui desktop (if installed). Try typing "gdm" if ubuntu-desktop or xubuntu-desktop is installed.

---

### Post by zoon_unit on 2006-06-20
I tried typing startx and got some funky hatched screen with a primitive terminal screen at the top.  Rebooted and tried "sudo gdm" and got "config= ! null" errors and a final "segmentation error"

????

---

### Post by zoon_unit on 2006-06-20
Okay, from what I can discern from the error messages when typing startx, there's obviously more to setting up the desktop than simply running "apt-get install ubuntu-desktop"

I also ran "sudo dpkg-reconfigure -phigh xserver-xorg" which seemed to terminate successfully.  Judging from the errors I received, it looks as if the desktop file system hasn't been built properly.

Any ideas???

---

### Post by greenstar on 2006-06-20
OK, I might be onto something.

> Rebooted and tried "sudo gdm" and got "config= ! null" errors and a final "segmentation error" 

I noticed you used

```
sudo gdm
``` 
you don't need sudo (root privilege) to start gdm for a user

just do:

```
gdm
``` 
to log in as a user.

Ubuntu doesn't allow root to login to the desktop.

If I understand the implications of that correctly, that's why Ubuntu uses ```
sudo
``` instead of ```
su
``` like some other distros.

Hope this helps,
greenstar

---

### Post by zoon_unit on 2006-06-20
Okay, I tried just typing "gdm" and got the following error message (6 times)

"(process:4605): GliB-CRITICAL **: g_hash_table_lookup assertion: 'hash_table != NULL' failed"

---

