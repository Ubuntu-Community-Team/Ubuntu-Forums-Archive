---
title: "Unable to install, hangs on boot screen"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by Anvh on 2010-10-26
Tried to install Ubuntu Netbook 10.10 on my Asus R2H next to Windows 7.

I get it so far that it see the USB and loads it.
I get the Ubuntu logo with the balls underneath it, those balls change from red to white.
That goes on for a minute and then all the lights go on on the PC and all the balls turn red under the logo and Ubuntu doesn't appear to do anything.
There is no sign off activity from the CPU, Harddisk or the usb drive but I waited for 15 minutes just in case.

I've tried it with the suggest USB loader/installer, with unetbootin and bruned the iso on a DVD with the same effect.

Could someone please suggest other things to try or know a solution?

Thank you in advance.

---

### Post by dino99 on 2010-10-26
what you've describeb is plymouth, so that mean installation is done, dont you ?

you might be able to open a terminal with: alt+F2
then run:
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

startx

---

### Post by Anvh on 2010-10-26
Thank you dino99

I've no idea if it's done, i only see the logo and it seems like it's preparing to install.
Haven't been prompted with any question about how to install or what language to use.
This is the window i mean.
I've the feeling it hangs up just before that.
[IMG]http://www.ubuntu.com/sites/default/files/active/maverick/trial_01_medium.jpg[/IMG]

This is partially what i see.
I only see the black part with the logo, don't know if i'm missing the other part of the screen or not.
[IMG]http://www.ubuntu.com/sites/default/files/active/maverick/install_09_medium.jpg[/IMG]

Could it be the screen resolution of the R2H is too low?

---

### Post by Anvh on 2010-10-26
Did a startup from USB with the desktop PC and it worked so the information on the USB seems to be correct.
Indeed after loading you see the selection screen i posted.

When loading i pressed f2 and wrote down the code where it stopped.

[59 .684906] HDA intel 0000:00:1b,0 irq42 for msi/msi-x
[59 .710214] HDA intel 0000:00:1b,0 setting latency timer to 64

It's not responsive to any input at that point but if i remove the keyboard and plug it in it sees that and it seems to install the drivers for it.

---

### Post by Anvh on 2010-10-27
Installed 10.04 without a hitch so will try to update that to 10.10
Hopefully that works :)

---

### Post by allen_b on 2011-01-11
I had exactly the same problem on openSUSE 11.3 with the same error message.  I have assumed the problem is with Xorg.

How did you go with updating from 10.04?

---

