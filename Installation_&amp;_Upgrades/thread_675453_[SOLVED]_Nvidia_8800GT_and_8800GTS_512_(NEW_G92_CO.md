---
title: "[SOLVED] Nvidia 8800GT and 8800GTS 512 (NEW G92 CORE) not supported by 7.10 graphic i"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by Shadow ZERO on 2008-01-22
Could a mod or dev please verify that this is in fact the case and sticky this thread?  I'm sick of seeing this problem posted over and over again and never being solved.  Well I've done so!  Now its up to YOU to verify I'm right and STICKY IT!!!

EDIT:  If you have a new 8800GT/GTS, and are getting A BLANK SCREEN AFTER THE INSTALLER SPLASH MENU, then you are having this problem.  Please add support to this thread by replying to it so it can be stuck!!!

---

### Post by Craigus on 2008-01-22
> Well I've done so

Are you planning to share your solution ?

---

### Post by bmclaurin on 2008-01-22
Would love to know your solution. Please share. I'm having this problem and don't know how to proceed.

---

### Post by Rice_slayer on 2008-01-22
Great, So it ISNT just me having this issue. I have an XFX 8800GT and the set up to install won't start due to some graphic thing. This sucks!!! Is there any linux I can use that supports my card? Honestly, I hate windows vista, I just use it for Direct X 10 :P.

Side note, does it matter if the video is hooked up via Analog or DVI? As I only have DVI, just wondering and does me having a Q6600 quad core have anything to due with 7.10 not working?

---

### Post by JayBee808 on 2008-01-23
Have you tried disabling the "splash" and "quite" options when you start the LiveCD?  My 8800gts always hangs when trying to load the usplash screen.  If I disable it everything works fine.

---

### Post by bvanaerde on 2008-01-23
This thread is rather confusing... 

I'm thinking of installing Ubuntu 7.10 to my new PC (with 8800GTS 512MB), and if there's already a solution available, I'd like to know it.
Saves me the trouble & time to figure it out myself :)

---

### Post by cleaves on 2008-01-23
Hi - I have an 8800 GTS 512 and came here looking for answers to the same issue, after installing the Nvidia driver on 64 bit 7.10 it would boot to a blank screen and reset to default graphics driver.
I commented out any references to "splash" and "quiet" in the boot loader and it still happened. At least it reverted to low-graphics mode though.
The next time it reverted to the default driver I changed the screen model under "Screen and Graphics Preferences" to "LCD Panel 1280x1024" (this is all mine is capable of) and set the resolution to 1280x1024, as Ubuntu had just defaulted to "Plug 'n' Play" at 640x480 on install. As soon as I applied this it switched immediately to the Nvidia driver without even asking and I now seem to have a healthy screen resolution and openGL support. I guess the Nvidia driver just can't handle the archaic screen resolution. Hope this helps.

---

### Post by PmDematagoda on 2008-01-23
For anyone wanting to know how to use the Nvidia 8800GT on Ubuntu, this [thread]("http://ubuntuforums.org/showthread.php?t=665018") can be rather helpful.

The reason this thread may not have been stikyied may be due to the fact that the Nvidia 8800GT is not a very widely used VGA card and that it currently faces problems on Linux due to the VGA card being rather new, so as time goes on, the Nvidia 8800GT should work on Linux without having to resort to the solutions given in the thread.

---

### Post by jhhdk on 2008-03-04
Bump

---

### Post by PmDematagoda on 2008-03-04
> **jhhdk said:**
> Bump
What are you bumping this thread for? You are not the OP of this thread therefore you should either specify your problem in this thread or (more recommended) post your problems in a new thread.

---

### Post by Johanneke on 2008-04-14
Well I guess the problem is still not solved, at least I did not find any solutions...
I have exactly the same problem here. I have a 8800GT, using a Q6600 quad core on my Assus P5K premium board. When I boot with the live CD for Hardy or Gutsy, all I get is a blank screen.

I tried more then one CD just in case one of them was broken, all had the same problem.
I did not tried the alternate CD yet, but I will do that just to see if it works.

I am not one of the lucky few with an spare (old) video card to test and install Ubuntu, so I have too wait till there is a solution, which I hope will come soon...

---

### Post by mwilliamsr on 2008-04-14
I had the same issue... (Nvidia 8800GTX 512' Q6600 CPU EVGA MB)
FIX:\
Try using "F6" in the startup menu and remove -quit -splash from the boot line. This will stop the splash screen from hanging during boot up. Once the system is installed, modify you menu.1st file the same by removing the -quit -splash from the menu entries...//


 No system work great... And the 3D graphics are awesome...

---

### Post by h0ax on 2008-04-16
problem is not solved.  but there is a workaround

use a text-based install disc when you install.
then, go into recovery mode from GRUB
then run

'vim /boot/grub/menu.lst' 
scroll down to find the option where it shows the kernel that you will be booting, look for "quiet splash" at the end of the line, go to the end of the line (push END key and then go back left with arrow) then push INSERT key to insert -- type "no" in front of splash so it now reads "nosplash" 
hit ESC
type :wq
hit enter
type reboot
hit enter
bingo (:

i am on 8800GTS

---

### Post by nbayiha on 2008-04-30
i think i solve the problem following this , i already post the way i did it in that thread. Hope it will help you 

[http://ubuntuforums.org/showthread.php?t=765985&highlight=nvidia+8800gts&page=3](http://ubuntuforums.org/showthread.php?t=765985&highlight=nvidia+8800gts&page=3)

---

