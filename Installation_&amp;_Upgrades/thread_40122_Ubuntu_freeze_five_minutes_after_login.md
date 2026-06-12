---
title: "Ubuntu freeze five minutes after login"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by oli-net on 2005-06-07
Hello everybody

I've installed Ubuntu that version of Ubuntu :[ubuntu-5.04-install-i386.iso] and everything would be good. But five minutes after login into the system, Ubuntu is freezing... No mouse, no keyboard, everything is stopping.
All I can do is reset the PC  ](*,) 

I tried to update the system, but during the download, after a while Ubuntu freeze.
Is someone have an idea on how can I solve that problem, please?

Thanks in advance for any help.
I'm new to that distrib, and I love it for it simplicity to install.

Many thanks!

---

### Post by oli-net on 2005-06-07
Hiii,

I've read that thread : [http://ubuntuforums.org/showthread.php?t=35455](http://ubuntuforums.org/showthread.php?t=35455)

My graphic card is ATI Radeon 7000 with 64 Mo, I'm going to try to install the ATI drivers to see if the problem is solved.

Soon...

---

### Post by Arthemys on 2005-06-07
Have you tried any keystrokes such as CTRL-ALT-Backspace [Kill X] or even CTRL-ALT-Del ?

An idea is that your X server may be seizing up for lack of driver support or something else.

---

### Post by oli-net on 2005-06-07
I've changed my driver name to vesa, but it steel freezing. ](*,)  ](*,)  ](*,) 

@ arthemys : You said :An idea is that your X server may be seizing up for lack of driver support or something else.
How can I change that!? I'm totaly new in Ubuntu.

CTRL+ALT+Backspace or CTRL+ALT+DEL do not do anything

Many thanks.

---

### Post by Arthemys on 2005-06-07
Long shot but... Bad hardware, do different linux distro's do the same thing?

---

### Post by oli-net on 2005-06-08
Hii Arthemys,
Yes, I've tried different Linux distro's and all were OK. My last distro was Mdk 10.1 and it was OK during the last six month. I'd let it for UbuntuLinux because of the difficulties to setting up certain things.

Thanks

---

### Post by paulius on 2005-06-14
It seems that I'm experiencing the same problem on my computer also!

I've burned the newest Hoary intall CD. Installation was flawless and no error messages were reported. (Another weird thing is that it didin't ask for my root password... is this normal? Maybe I've got a corrupted CD. Please someone inform me on this!)

What happens is that X starts nicely, I then type in my username, password and then I go to another screen with the wide Ubuntu logo. Several seconds later: it freezes.

And it freezes rock solid, no mouse imput, no keyboard, no CTRL+ALT+DEL, no killing X, no changing terminals and no kernel panic. Only way to get the computer alive is with the reset button.

This freezing happens every time I login into Ubuntu.

Specs:
3GHz Intel Pentium 4 775
1GB DDR RAM
Ati X600 256mb
SATA 80GB Maxtor 7200rpm with 8mb cache
Sony DVD writer
Sound blaster live! Platinum 5.1

Any help at all would be useful for me!

EDIT: NVM, fixed it with this link: [http://ubuntuforums.org/showthread.php?t=35455](http://ubuntuforums.org/showthread.php?t=35455)
One quick note for newbies: the author of the post once did a typo on the "xorg.conf" filename...

---

### Post by sgbooth on 2005-06-14
There are some problems with X.org & Nvidia and Ati drivers.  I was able to fix it by disabling some stuff in xorg.conf.  

1. sudo gedit /etc/X11/xorg.conf
2. Look for Section "Devices" 
3. Insert Option "RenderAccel" False into the "devices" section
4. Look for Section "Modules"
5. Disable GLX by commenting out Load "GLX"
6. Logout and restart X

This worked for me

sgb

---

