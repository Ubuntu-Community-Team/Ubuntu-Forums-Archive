---
title: "Ubuntu can't start after upgrade from 9.10 to 10.04"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by osced on 2010-06-06
Today I decided to upgrade from 9.10 to 10.04, so I used the upgrade ubuntu button and everything seemed to work during the upgrade, but when I did the reboot the computer got stuck with a black screen with some green dazzles. I tried to start ubuntu with another Kernel but it didn't work. I tried the recovery mode to start ubuntu with the minimal graphics mode, but I got a error that they didn't find a a screen and it also complained about 'no usual configures' .
It looks like ubuntu finds my graphic card, because when I used 'lspci |grep VGA' i got the specification for my graphic card.
I hope someone could help me with this, I haven't any clue about what did go wrong.


---------------------------------------
My computer specs
AMD 64 X2 4400+
2 Gb Ram
Nvidia GeForce 7800 GTX

---

### Post by davidmohammed on 2010-06-06
at a guess the first thing you should try is to add nomodeset to your grub...

after the bios screen press shift to display the list of kernels - this is your grub.  Press e.  Navigate down to the line containing quiet splash.

add nomodeset immediately before quiet splash

if that doesnt work, repeat but add

nomodeset xforcevesa

---

### Post by osced on 2010-06-06
I've already tried the 'nomodeset' before, but I tried the other one and it didn't work. I still got the black screen with some colorfull dots, who seems to move if I use my keyboard.

---

### Post by davidmohammed on 2010-06-06
suggest boot to recovery mode and drop to a terminal

see if there is a file called /etc/X11/xorg.conf

rename it and reboot (remember to include nomodeset xforcevesa) as your boot options.

---

### Post by osced on 2010-06-06
I tried to do so, but it didn't work either... I'm wondering if it's something wrong with my graphic cards, but everything worked fine in 9.10, so it shouldn't be any problem with that. So maybe it's a problem with the installation, I tried the fix package in the recovery mode, but it didn't work  because it look like I can't connect to my router.
I've also tried 'sudo dpkg-reconfigure xserver-org and that didn't work either.

---

### Post by davidmohammed on 2010-06-07
ok - one further boot parameter to try -

add

fb=false

to the list

i.e. nomodeset xforcevesa fb=false

if that doesnt work, can you repeat the above but choose recovery mode and when prompted choose safe graphics.

---

### Post by osced on 2010-06-07
I tried that with no success, but according to GRUB this commands aren't working commands. I tried the 'tab' 'tab' to get all working commands and no of these commands was there.

I also checked Xorg.log and it looks like the real problem are that they can't find a screen mode that works. Maybe it would work if I would edit my xorg.conf file and put in a screen resolution that I'm using ?

EDIT:

I've tried to start the Live CD for 10.04 and it seems to work, so maybe it's something wrong with the installation ?

---

### Post by davidmohammed on 2010-06-07
the tab - tab doesnt display all the boot options possible.

Having googled around there doesn't seem to be a consensus for the graphics card you have.  Some people have had success with some of the options you've tried above.  Some haven't.

Others suggest boot with one of the following options: 
vga=788
vga=791
vga=837

n.b. again some suggest booting with one of the above in combination with nomodeset.

Some have suggested booting into recovery mode and selecting fail-safe graphics...

Sorry, have now run out of suggestions

---

### Post by osced on 2010-06-07
Thanks for your help, I will try your last suggestion and If it doesn't work I will try to reinstall Ubuntu and hope it would work with a clean install.

---

