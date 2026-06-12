---
title: "I Have Tried 3 Times, Still No Luck.."
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by JayDeePlus on 2008-03-29
I Have downloaded Ubuntu 7.10 and burned the iso to a cd. Booted to CD, was able to bout and operate in Ubuntu live. Tried installing, After installation was complete attempted to boot off of hard drive. Black screen, Operation System Error: . Put Cd back into computer, was able to boot back into ubuntu live. tried several more tries at installing and booting from had drive, last time tried, i was able to get the grub to come up and tried to boot from ubuntu recovery., After running recovery, still i'm not able to boot from hard drive. is there something i can do?, since i have 2 cd burners, is there a way i can redownload and/or reburn a copy to fix this problem? please i'm not sure what to do.

---

### Post by jimv on 2008-03-29
I couldn't get 7.10 to boot on my machine. The 8.04 (Hardy Heron) beta version works though.  Maybe give that a try?  To me it seems more stable than even previous final releases that I've used...but that's just on my laptop.

---

### Post by ZALMAN on 2008-03-29
Have you verified the cd for errors. This can be done at boot. Possibly the image was not properly burned, there are open source burners available for windows at _[http://sourceforge.net/](http://sourceforge.net/)_ or you can receive cd's directly at ubuntu launchpad.

---

### Post by Pumalite on 2008-03-29
Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on iso, burn at 4x or less on CD-R, Check CD integrity after burn and before install.
The Alternate CD is a better installer.

---

### Post by JayDeePlus on 2008-03-29
i have  computers........... my 2.6 ghz p4 machine is what im trying to install it on. the machine already had XP on it..........but when i tried to install 7.10..............it said it found windows setting and was going to import...........but after it partion it's like the setup just stops............i ran the install again..............and it got to the screen that said installition complete.............please restart and remove CD............so i do...........and it tries to boot............it say starting up...........then below that it say loading...........but then it hangs at a black screen after that...............is there something i 'm doing wrong?

---

### Post by Pumalite on 2008-03-29
Ctrl+Alt+F1 to get command line:
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver.
Then: startx

---

### Post by JayDeePlus on 2008-03-29
i'mma try and burn the new 8.04 hardy heron to a cd and try to boot from that..........but what else could i try if this don't work............

---

### Post by Pumalite on 2008-03-29
Let's see what you have. Post:
lshw

---

### Post by JayDeePlus on 2008-03-29
i've burned 8.04 hardy to a disc with burner speed at 6x (because for some reason it runs into a problem when i burn at 4x). this time when i put it into my second computer and try to boot, instead of getting the Ubuntu logo (which is what my other burned copy of ubuntu does, but i think it's a problem with the installed with the first copy i made) it has a calder trademake and goes though a series of codes, then it's stops at a prompt as if it's waiting for my input, but i don't kno what to input. I was expecting the ubuntu logo and a install or start option. So, before i put the new copy into my second computer i ran a check on the integrety of the CD after i burned it, and it report no problems. 

I am able to put the first copy into second computer and but off of to ubuntu live, also (i'm not sure how much help this will be) i am able to route through firefox on the ubuntu live. but if you've read ne of the previous post, after i run ubuntu install, i try to boot off of hard drive with ubuntu CD in drive, and it hangs at a black screen. Is there some type of compatibility problem here or could it be the copy of ubuntu i have. (NOTE: the first copy i have is version 7.10). If someone can help i would greatly appreciate it, because i have before in the past gotten this to work on a previous computer i had. any insight is greetly appreciated at this point

---

