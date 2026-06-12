---
title: "Problem with Feisty Installation on my laptop :("
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by kratzz on 2007-04-21
Hello people, I'm new to fairly new to the Linux world, but I know my way around.
And now to tell you guys my problem:
- I downloaded the new Ubuntu 7.04 and imideatly installed it on my Desktop with no problems.
- Desktop specs: AMD Duron 1.3 Ghz/512 MB DDR/ATI Radeon 9520 128 MB/80 GB ATA HDD.
- But when I try to install Feisty on my Laptop, this is what happens: I put the Ubuntu CD in the CD-Rom, the laptop sees the disk and boots from it, I choose the first option (to run the Live CD and install Ubuntu) and the orange bar goes from side to side then, the screen gets black and it loads up Ubuntu in the text mode (not the way it happened on Desktop) and then i get the Error Message: X Window system failed to start, and then it tells me to restart... .:(
- Laptop specs: Acer Aspire 5112WLMi/AMD Turion 64 x2 1600 Ghz/512 MB DDR2/ATI Mobility Radeon X1300 128 MB Dedicated+128 MB Shared/80 GB SATA2 HDD/15.4 WXGA Screen.
- What is the problem?? - Is it the Acer Bios? Is it the video card? Please help me guys! Feisty works like a charm on the Desktop and it's awesome... but i need it on my laptop.
- Oh, and btw if I choose the option "Run Ubuntu in safe graphics mode" when booting from the CD, it still doesn't work.

---

### Post by bran on 2007-04-21
Duron is 32 bit isnt it?  you will need the amd64 desktop image for the the laptop at least. the vid card may need configuration but it should work from what I have been hearing. I run an Acer but its intel vid/proccesser.

---

### Post by klaim on 2007-04-21
is not arch problem! you can use 32bit OS on the 64bit processor.
I have same problem too!
My laptop doesn't start with 7.04 install cd. X fails. both drivers 'ati' and 'vesa' does not work. But... if i use framebuffer, i can start X with 'fbdev' driver. But i want to get work 'ati' driver. By the way... when i have installed with 'fbdev' i'm tryed to use 'fglrx' - same bag! 

This is the first release, when i have so big problem :(. Breezy,Dapper, Edgy just works out of the box.


lap desc: Acer Aspire 5024 wlmi. amd64, 2Gb ram, Ati X700.
i tryed desktop-amd64 and just i386 desktop images.

---

### Post by bulldog on 2007-04-21
You can try to reconfigure xserver```
sudo dpkg-reconfigure xserver-xorg
```
If this want solve your problems install the restricted modules and your graphics driver.
You need to know which kernel you have though```
uname -a
```
This wil give you something like```
bulldog@AMD64:~$ uname -a
Linux AMD64 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
bulldog@AMD64:~$ 
```

Install the restricted modules ```
sudo aptitude install linux-restricted-modules-2.6.20-15-generic
```
Use your own kernel version ofcourse.
Install the graphics driver for your card,I only have some knowledge of nVidia,and reboot.
```
sudo aptitude install nvidia-glx
```

After reboot,and it fails again,take a look at the xorg.conf file,to see if the driver is properly listed,and your resolution as well.
```
sudo nano /etc/X11/xorg.conf
```
If you alter something in the file,leave it with ctrl-x and enter to save the file.

---

### Post by K1T on 2007-04-21
I have same problem-

hardware: Acer Aspire 3100  /  ATI Mobility Radeon

Ubuntu Edgy 6.10 worked fine. Now I have same problem you described. In the beginning it gives BIOS BUG #81 if you look quickly.

---

### Post by house7 on 2007-04-21
Well, right now i don't have any problem with my laptop driver, but my problem right now is all my typo in ubuntu is SQUARE, I can't read anything. All my text in desktop, windows even the clock is turn to square.. i don't know what happen.. *i just upgraded to feisty..*

anybody know why and how i can fix this??? thanks

---

### Post by Dr_Deadmeat on 2007-04-22
> **kratzz said:**
> Hello people, I'm new to fairly new to the Linux world, but I know my way around.
And now to tell you guys my problem:
- I downloaded the new Ubuntu 7.04 and imideatly installed it on my Desktop with no problems.
- Desktop specs: AMD Duron 1.3 Ghz/512 MB DDR/ATI Radeon 9520 128 MB/80 GB ATA HDD.
- But when I try to install Feisty on my Laptop, this is what happens: I put the Ubuntu CD in the CD-Rom, the laptop sees the disk and boots from it, I choose the first option (to run the Live CD and install Ubuntu) and the orange bar goes from side to side then, the screen gets black and it loads up Ubuntu in the text mode (not the way it happened on Desktop) and then i get the Error Message: X Window system failed to start, and then it tells me to restart... .:(
- Laptop specs: Acer Aspire 5112WLMi/AMD Turion 64 x2 1600 Ghz/512 MB DDR2/ATI Mobility Radeon X1300 128 MB Dedicated+128 MB Shared/80 GB SATA2 HDD/15.4 WXGA Screen.
- What is the problem?? - Is it the Acer Bios? Is it the video card? Please help me guys! Feisty works like a charm on the Desktop and it's awesome... but i need it on my laptop.
- Oh, and btw if I choose the option "Run Ubuntu in safe graphics mode" when booting from the CD, it still doesn't work.
You just have to edit your /etc/X11/xorg.conf file and then you have to scroll down to the 'Section "Device"' and change the driver from ati or fglrx to vesa... when you have done that you should be able to boot in, but with very limited functions.
After you are able to boot into ubuntu you can install ATI's official drivers and things should work.

Hope this helps you =)

---

### Post by bclinton on 2007-04-23
Same problem here. This is one reason why Ubuntu will never really get off the ground. We are trying to get normal users to switch but when a normal user trys to install this on a normal laptop with a normal ATI video card he has to jump though 999 hoops to get it to boot.

---

### Post by Judicata on 2007-04-23
Although it doesn't apply to OP: if you are upgrading to Feisty, and you are using the fglrx driver for an a Radeon 9000 card or older, then it won't work.  You have to switch to the open source drivers.  ATI dropped support for these "older" cards (yeah, right, I got mine 2 years ago), and the older ATI driver doesn't work with the new x.org.

---

### Post by equilibrium on 2007-04-24
I have the same problem, I might download the alternate install cd :(

I might try plugin in my monitor tho, just in case it is trying to use the vga output instead of the laptop screen :(

---

### Post by equilibrium on 2007-04-24
I'm posting this on my laptop on ubuntu feisty now :)

To install I needed to plug in my VGA monitor.
Once installed just intall the restricted drivers. (System>Administration>Restricted Drivers Manager)

Then when it asks to reboot, reboot and unplug the VGA monitor :) then it works, but the res isn't right so you just need to edit the xorg.conf adding the 1280x800 mode.

Then reboot or logout to gdm and ctrl+alt+backspace to kill X :) that's all you need to do.

GL :)

---

