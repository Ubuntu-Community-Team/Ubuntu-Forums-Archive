---
title: "[SOLVED] I don't see splash screen after upgrading to 7.10"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by NewbieSLP on 2007-11-11
Hello all, here is my situation: I have a PC with Pentium IV at 3.0 Ghz, 1Gb of RAM, 80Gb IDE hard disk, 180Gb SATA hard disk, motherboard is ASRock P4VM800, floppy, DVD Burner and DVD Combo. I used to use Ubuntu 7.4 with no problems at all, I was very happy (no compiz fusion effects as my motherboard's video chip doesn't support xlg).

Then upgraded to Ubuntu 7.10 and after being properly installed, when I booted I just couldn't see the splash screen. In its place, monitor (HP Pavillion M50) show a totally black screen with a message "Right resolution?", then it showed Ubuntu's desktop and everything worked fine. So I thought maybe I needed a Nvidia video card to be able to see the splash windows again, so I bought a AGP Nvidia GE-Force FX5200 and plugged the monitor to it. Problem did not solved, indeed, it became worst. I still see the black screen on the monitor, (just after the grub) when booting in place of splash screen and when I see Ubuntu's desktop everything seems like dancing or moving horizontally a little, specially when displaying and mousing over menus and this last thing is very upsetting for my eyes, they get very tired  :(

So I thought maybe I should check monitor configuration at "Sistem >> Administration >> Screens and Graphics". I downloaded Nvidia proprietary drivers and activated them, set monitor HP Pavillion M50 at 1024*768 at 50mhz and I still see lines "dancing". If I set it to 60mhz screen looks awful with many-many-many micro dark lines all along the screen (though it doesn't dance anymore!).

I'd like to know what I am doing wrong, and repeating: I used to use Ubuntu 7.04 with no problems at all with the same monitor, problem begun just when upgrading.

Thank you very much for your guidence and excuse my bad english (I've never studied it and my native language is spanish).

**NewbieSLP** :(
[www.comohagoenlinux.blogspot.com](www.comohagoenlinux.blogspot.com)

---

### Post by rainwalker on 2007-11-12
I'm not sure about your resolution/graphics issue, but I do know that the splash screen in gutsy is not shown by default

---

### Post by VgForce on 2007-11-12
try pressing crl+alt+f1. i had same problem but it was fix somehow :D .

---

### Post by Tony3286 on 2007-11-12
I had the same problem - took a few days and a few good people to help me. Basically your resolution was changed when upgrading to Gutsy , which causes the resolution warning. I bet, you boot up, get the resolution warning, wait about 20 seconds and your log in screen  comes on, you log in and everything is fine. First I would suggest you go to System - Start manager and check and see if in fact the splash screen was turned on or off - bet its on and its the resolution issue.

Read my post - theres 3 pages -  it should definitely help
[http://ubuntuforums.org/showthread.php?p=3732578&posted=1#post3732578](http://ubuntuforums.org/showthread.php?p=3732578&posted=1#post3732578)

Tony

---

### Post by Tony3286 on 2007-11-12
One OTHER thing - stay OUT of **"Screens and Graphics"** very buggy - caused me more problems

---

### Post by NewbieSLP on 2007-11-13
Hello Rainwalker, VgForce and Tony3286, thank you for your kind answers.

VGFORCE: I tried crl+alt+f1 at startup and well, as you say and I see text mode, it's not so bad after all and it's better than my monitor screaming!

TONY3826: You are right! That' is exactly what happened to me! I wouldn't say my resolution was *changed* as I had to make a clean install because trying to upgrade from using 7.04 froze my PC and always said that didn't find files or repositories, so I backed up my data and make a clean install. I did what you said: Go to System >> Administration >> "Entrance window" ("Ventana de Entrada", translated literally from Spanish as I can't find "Start manager"). I activated splash screen on System >> Preferences >> Splash Screen (I downloaded that application). Ok, now I see just some seconds of the Buddha splash screen (my favorite) and it's ok, but seconds before it appears, monitor keeps saying: SELF DIAGNOSIS, PC DISPLAY SETTINGS CORRECT? (I'm sorry, it' doesn't mention anything about resolution like I said before, this is what actually says).

I followed the steps given to you by ERGINEMR in your previous post, changed my usplash.conf and finally I see Ubuntu logo and the progress bar!

Thank your very much for your time!!

Best from México,
NewbieSLP

---

### Post by NewbieSLP on 2007-11-13
PS
I also did what it's said on: [http://ubuntuforums.org/showthread.php?t=604216](http://ubuntuforums.org/showthread.php?t=604216) said by **Eye208**

"The proper method to change the splash screen resolution is to edit /etc/usplash.conf and then run

sudo dpkg-reconfigure -phigh usplash"

Now I see the Ubuntu Logo and the progress bar.

---

### Post by shafin on 2007-12-04
> **NewbieSLP said:**
> PS
I also did what it's said on: [http://ubuntuforums.org/showthread.php?t=604216](http://ubuntuforums.org/showthread.php?t=604216) said by **Eye208**

"The proper method to change the splash screen resolution is to edit /etc/usplash.conf and then run

sudo dpkg-reconfigure -phigh usplash"

Now I see the Ubuntu Logo and the progress bar.
Thanks

---

