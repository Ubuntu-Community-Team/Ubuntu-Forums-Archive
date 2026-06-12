---
title: "[SOLVED] Upgrade- cannot pass login screen"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by kolicha on 2008-05-27
Hi, 

I installed ubuntu 7.10 from cd 2 days ago. I have upgraded ubuntu to 8.04 by going to system>admin>update manager. 

However, now i cannot boot up ubuntu. I am dual booting with windows vista and i have the os selector. Unlike in 7.10 i have two non recovery options to chose for ubuntu:

ubuntu 8.04, kernal 2.6.24-16-generic and
ubuntu 8.04, kernal 2.6.22-14-generic.

The former is the experience the problems i am describing the latter doesn't recognise my graphics card. 

So getting to the point, if i choose ubuntu it takes me to the login screen. I login fine then the screen goes blue and a cream window appears in the top right of the screen. If i put the cursor over this window it changes to the "I". Ubuntu will not progress any further with the booting. 

Screen shots:
[[IMG]http://img366.imageshack.us/img366/4047/dsc00148lj1.th.jpg[/IMG]](http://img366.imageshack.us/my.php?image=dsc00148lj1.jpg)

[[IMG]http://img258.imageshack.us/img258/4240/dsc00149ny3.th.jpg[/IMG]](http://img258.imageshack.us/my.php?image=dsc00149ny3.jpg)

I tried booting in recovery mode and running the fix and every time i run it, it says: "x server-org postinst warning: overriding possible customized configuration file; backup in /etc/x11/xorg.conf.20080527171354"

Specs:
Graphics Card: Nividia geForce 8400M GT GPU
CPU: dual core 1.8GHz
Ram: 2GB

Any ideas on what i can try? 
Thanks

---

### Post by markoloka on 2008-05-27
Can you login in textmode aka ctrl+alt+f1??
Try there: startx. Try also sudo apt-get update.

---

### Post by kolicha on 2008-05-27
Thanks for the fast response. 

Yes ctrl+alt+f1 does work

Startx on ctrl+alt+f1 says:

Fatal Server Error: Server is already active for display 0 if the server is no longer running, remove /tmp/.x0-lock and start again

startx in recover and using root terminal comes up with:

> 
log file /var/log/Xorg.0.log
Module "12c" already built in
Module "ddc" already built in
Module "ramdac" already built in
Failed to initialise GLX extention (compatible Nividia X driver not found) 
Expected keysym, got xf86kbdLightOnOff line 70 of pc
Expected keysym, got xf86kbdBrightnessDown line 71 of pc
Expected keysym, got xf86kbdBrightnessUp line 72 of pc
Atom 4 card324, unsigned long 4
Expected keysym, got xf86kbdLightOnOff line 70 of pc
Expected keysym, got xf86kbdBrightnessDown line 71 of pc
Expected keysym, got xf86kbdBrightnessUp line 72 of pc

waiting for x server to shut down.  Free Font Path: FPE /usr/share/fonts/x11/misxrefont is 2 should be 1; fixing


apt-get update from ctrl+alt+f1 returned:

> 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en-GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en-GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en-GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en-GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse packages
Reading Package List...Done



So from the startx. Shall i use "sudo /etc/init.d/gdm stop (to stop the xserver)", (Got code from thread below mine) then try startx again? Or try removing the file it told me to? Or something else?

Thanks

Edit: As an update, i left ubuntu for a while on that screen, when i came back it had loaded up. However i have this error message waiting for me:

[[IMG]http://img377.imageshack.us/img377/6145/errorjk5.th.jpg[/IMG]](http://img377.imageshack.us/my.php?image=errorjk5.jpg)

Edit 2: I enabled the restricted drivers and rebooted and waited this time. Still takes ages to boot up, the cream/white rectangle in the corner is the error i showed you. Things like wobbly windows and burn on close are working. So any ideas how to get rid of this error message and make booting quicker?

Thanks

---

### Post by kolicha on 2008-05-27
Fixed:

[http://depratama.wordpress.com/2007/12/19/ubuntu-error-starting-the-gnome-settings-daemon/](http://depratama.wordpress.com/2007/12/19/ubuntu-error-starting-the-gnome-settings-daemon/)

---

### Post by boblq on 2008-08-09
I have this same problem. I do not understand your answer in the reply that follows. Could you elaborate? 

TIA,

BobLQ

---

### Post by kolicha on 2008-08-09
I'm no expert with Linux, but what I did was leave it at the blue screen for a while. When I came back to it, it had booted up with the error message I had shown in my post. I then did a bit of searching and found:

[http://depratama.wordpress.com/2007/12/19/ubuntu-error-starting-the-gnome-settings-daemon/](http://depratama.wordpress.com/2007/12/19/ubuntu-error-starting-the-gnome-settings-daemon/)

"1. add two line in file /etc/network/interfaces:
auto lo
iface lo inet loopback

and commenting out all entries with IPv6
then type sudo ifup lo on terminal
and reboot linux box (ubuntu 7.04/feisty fawn)

2. Go in the sound preferences and disable ESD"

Following the first solution fixed my problem.

---

