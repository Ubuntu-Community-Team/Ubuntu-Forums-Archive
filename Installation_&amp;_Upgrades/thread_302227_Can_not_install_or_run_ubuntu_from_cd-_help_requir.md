---
title: "Can not install or run ubuntu from cd- help required"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by iiyama on 2006-11-18
Hi there, 

Iv just downloaded ubuntu file ubuntu-6.10-desktop-i386.iso. 
Hash check was then done, it was a match. 
Next the iso file was burned to CD-R using ImgBurn. This also completed successfully(the cd auto ran on windows).

Now for the problem:
The Cd boots when restarting and shows the initial Ubuntu menu (start or install, start or install in safe graphics mode, check CD for defects etc...)
I choose the first option(start or install) and press enter.
Next i see a Ubuntu splash screen and a progress bar only(no other text is visible on screen)
The progress bar progresses almost to he end and stops just before the end.
I then see a fuzzy line across the progresses and nothing else happens. 
When i press enter or escape the tiny fuzzy line changes color or moves a bit. (sorry this bit is hard to explain in words).
pressing enter producess no other effect. 

Same thing happens when i run 'start or install in safe graphics mode'
I have also burned the CD a number of times

My system is Pentium 4 3.2GHz, 512MB ram, 320GB hard disk(raid 0), ATI radeon x850xt PE graphics card, 

I have taken pics of the process which i can upload if needed.

Thanks for reading.

---

### Post by emil_p8 on 2006-11-18
Have the same problem with the live cd on a amd64 pc with a Ati Radeon x700. 
BTW if i disable splash & quiet options or switch to a console, i see that it stops just at the end of bluetooth detection (rfcomm 1.7-something), if this may serve someone for debugging, also i don't have bluetooth on the machine. I can get to a console; but can't run X from there, even with dpkg --reconfigure xserver-xorg
Edgy otherwise works on this machine since i upgraded my 6.06 to a 6.10 and it fires up. Sorry, don't know of a solution by now; try the alternate install cd.

---

### Post by Ali_ix on 2006-11-18
I have the same problem and tried to install "fglrx" as Graphic Card driver and run x-server (i have x700)

search and read quids to install your Ati graphic card,
not really confusing... just some few steps. ;)

the easiest way is to have internet access and install needed packages using apt-get and reconfigure xorg.conf.

---

### Post by tutix on 2006-11-18
Hello, greetings from Croatia (Europe)

I have just downloaded Edgy Eft (Ubuntu 6.10), & i have the same problem. If i select first or second option in boot menu, i get this wierd lines instead of Ubuntu desktop or logon screen. In Ubuntu 6.06 i get the same lines when i pick the first option but if i pick second option (safe graphic mode) i am able to install ubuntu 6.06. Sorry for gramar mistakes, i have B (4)in English. :) 

My conf
AMD Athlon 64 3000+
1 GB DDR400
nVidia GeForce 6600

---

### Post by GhOsT003 on 2006-11-20
iiyama, I have the same problem that you posted 100% down to the last letter. Im new to Ubuntu but I am looking to find a fix for this problem, If I get my CD to work I will post how I did it.

p.s. If anyone else can help I wont say no because I may not be able to help since I am some what new to Ubuntu.

---

### Post by kvonb on 2006-11-20
Sounds like a graphics card driver problem, maybe your video card is too new for the opensource driver which is loaded by default.

There should be an option to boot in VGA mode, or reduced graphics mode.  Also look for a safe mode.

Once you have actually got to the desktop you can try installing the proprietary ATI driver (yes on the liveCD before you install Ubunto to your disk so that you know that it will actually work, it will save you headaches in the end) from ati.com, there are tons of guides on how to do that on the forum.

Regards,  Kev

---

### Post by PSyMastR on 2006-11-20
I also have this problem, only spec changes is my p4 is a 2.8ghz, ive got 1 gig of ram, and my ATI card is a x700.  5.04 installed perfectly fine, 5.10 did as well.  (long time ago when I used ubuntu on my pc, not just my laptop), now I wanted to go to 6.10 on my pc as well.  It loads, and stuff, except right when its about to load the live cd, it freezes.  Same issues as you guys.  Any luck anyone?  Is there anyway to install ubuntu without booting into the gui like in the older versions?

EDIT:  I tried 6.06, and it froze on mounting root file system... hmmm...

EDIT2:  On both 6.06 and 6.10, it always gives me a

hdb: cdrom_pc_intr: The rive appears confused (ireason = 0x01)

Then some irq 185: nobody cared (try booting with the irqpoll option) and when I do, it doesn't change anything... hmm...

EDIT3:  Tried without the quiet and splash options, and it says the xserver failed... :(

---

