---
title: "Display Problems"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by jordn on 2006-12-13
Hey there, this is my first post lol, so i hope i have done it in the right place. 

i am having many problems with ubuntu. first i downloaded edgy eft (6.10). installation went just fine, everything detected. until it came to rebooting,where i selected the ubuntu from the grub boadloader i installed. i press enter, and i see the ubuntu logo with a progress bar, but no text. when the progress bar finishes, i hear a drum-like noise and my screen starts flashing saying "out of range".

i thought that could be the cost of having "bleeding edge" software; having limited hardware support. so i downloaded dapper (6.06) LTS. same problem, but when i choose ubuntu from the grub bootloader i see the logo and text saying various processes are [ok]. when thats all loaded the display is scrambled!

i also have the same problem with kubuntu 6.06!

i hope someone help solve my problems. i have a little experience with commands from OSX, wether that makes any difference...

i really want to try edgy and be windows free by the new year! 



i will give you all my specifications: ](*,) 

AMD 64 3200+ (venice, SSE3)
1GB RAM (single channel)
XFX nvidia 6800XT 256MB

120GB HDD 

Partition scheme:

1st- windows mce2005 (40GB)
2nd- shagos swap (40GB) (HFS+, used for remotely backing up my aged mac mini g4)
3rd- ubuntu (35GB) ext3
4th- swap (1.5GB)

My display (since its causing all the problems)

DGM 15" widescreen running at 1024x768@60Hz

---

### Post by padre999 on 2006-12-13
Something is wrong with your X-configuration. It tries to run your monitor with a too high resolution, or too high sync rate. The setup details for the X-Server are saved in the file etc/X11/Xorg.conf

So there are several ways to try to fix that. 

Once you booted and you heard the sound of the drums press CTRL+ALT+F1 which will start another session and get you to the command line (Alternatively you could also boot in the "Recovery mode" I guess). Log in.

Then you can choose to either run the Xorg configuration script or you can try to edit Xorg.conf manually.

To run the script enter```
sudo dpkg-reconfigure xserver-xorg
```and go through the dialogue. Enter the right resolution and/or refresh rates for your Monitor when asked.

Then shutdown the computer and restart.

But you can also try to enter the right details into Xorg.conf manually. The advantage is that this way you won't mess with all the other settings in the file, except for the monitor settings. But then be careful not to make spelling mistakes etc.

How to to this? Have a look at [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) > Undetected Monitor Specs. Also in the "Subsection Display" of the Xorg.conf file make sure that there is no higher resolution than 1024x768 entered. After the changes, shutdown, restart...

Hope you find your way ;)

BTW: You have a 15'' wide-screen? And you run it at 1024x768? But 1024x768 is not a wide-screen resolution, no? It is a standard resolution. Then you should have quite a bad picture on your monitor (If it is a LCD) if you don't run the appropriate resolution.

---

### Post by jordn on 2006-12-13
hey there, thanks for your help.

but it still didn't solve my problem with Edgy.

i have tried the "dpkg-reconfigure" command, that allowed me to edit xserver, but when i reboot i still get the out of range error. and i have tried editing the xorg.conf file with nano. 
All the information is correct in there! resolutions, refresh rates, everything!

i have no clue what could be causing this.

any suggestions?

---

### Post by xabbott on 2006-12-13
Try checking out the contents of /var/log/Xorg.0.log?

---

### Post by jordn on 2006-12-14
right, i have checked the contents of the xorg.0.log file, and i am finding strange stuff, especially this line:

(II) NV (0) Supported Future Video Modes
(II) NV (0) hsize 1280 vsize 1024 refresh 60.

also, it gives me a list of resolutions that have failed (including the 1024x768 that i need) due to either hsyne or vsync being out of range. i can't quite remember exactly what it said but i will try and export the log file for you to see. 

please keep suggestions coming.

thanks again for your help,

jordn

---

### Post by padre999 on 2006-12-14
*Maybe* you are suffering from the problems that some people have with Nvidia 6... cards.

See [http://ubuntuforums.org/showthread.php?t=312764](http://ubuntuforums.org/showthread.php?t=312764)

But they just get a garbled mess on their screen, not a out of range...

---

### Post by jordn on 2006-12-14
thanks padre, you have been a great help. will try this when i get back from college. will let you know how it goes.

jordn

---

### Post by jordn on 2006-12-14
padre, i have done it, and it worked!!! i am now writing from firefox from edgy! thank you so much. 

one step closer to being windows free!!!

regards,

jordn

---

### Post by padre999 on 2006-12-14
\\:D/ \\:D/ \\:D/ 

But how did you manage? Did you install the Nvidia drivers?

---

### Post by jordn on 2006-12-14
i did sudo apt-get nvidia-glx to grab nvidia drivers for my card. it turns out the standard ones weren't too compatible, i think it was because it was trying to intitialise a Nvidia 6800 generic instead of my 6800XT (cut down version)... lol.

ah wells. 

thanx again!

---

