---
title: "live cd launching problem"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by phr3ak on 2007-03-21
Hey guys this is my firsttime to this forum

My computer specs:
Core 2 Duo 4300
Gigabyte 965p-ds3
1gb Corsair ddr2 memory (2x512mb)
2 x 160gb sata hitachi hard drives
7300gt Nvidia Card

I've tried loading both the 6.10 and 6.06 versions of the ubunto cds but it keeps freezing while trying to load. The screen goes blank after about a minute then starts give multiple messages that goes something along the line of "i/o buffer error." I have tried launching the cd on my other systems (which uses p4 chips or amd64 chips) and they load perfectly fine without any problems. Is there something about my system that's not compatible with ubunto? I looked through the incompatible list btw and its not updated.

---

### Post by ppatalano on 2007-03-21
When you boot the cd how far to you get? Do you get to the options menu where the first option is start/install ubuntu?

---

### Post by phr3ak on 2007-03-21
It got as far as the menu. I've tried both the first option (load or install ubunto) and safe graphics mode. For the 6.06 cd it showed that it stopped working as soon as it started to mount root kernel...then the series of errors showed up. the 6.10 cd didn't show what files were being loaded but it showed the errors about 1 min into loading live cd.

---

### Post by wpshooter on 2007-03-21
Have you tried choosing option 3, I think it is, to check the integrity of your Ubuntu CD by running the verification function ?

Boy, they really need to put that verification function as #1 on the menu list and put something beside it like "**DON'T DARE TRY TO INSTALL ****OR RUN THIS CD WITHOUT FIRST CHECKING THE INTEGRITY OF THIS CD**".

P. S. - I am not saying that that is the cause of your problem.

---

### Post by ppatalano on 2007-03-21
Do you have any other bootable cd's, besides ubuntu that you might be able to try? windows maybe or another version of linux?

---

### Post by ppatalano on 2007-03-21
Also make sure the jumpers on your cd/dvd drive are set properly. This could easily lead to not having a proper boot.

---

### Post by phr3ak on 2007-03-21
> **wpshooter said:**
> Have you tried choosing option 3, I think it is, to check the integrity of your Ubuntu CD by running the verification function ?

Boy, they really need to put that verification function as #1 on the menu list and put something beside it like "**DON'T DARE TRY TO INSTALL ****OR RUN THIS CD WITHOUT FIRST CHECKING THE INTEGRITY OF THIS CD**".

P. S. - I am not saying that that is the cause of your problem.

no defects detected. it has worked fine on my other systems (either p4 chips or amd64 chips) and it loaded fine on those systems but this one. 


"Do you have any other bootable cd's, besides ubuntu that you might be able to try? windows maybe or another version of linux?"

the only other one i tried is windows xp and it works fine

"Also make sure the jumpers on your cd/dvd drive are set properly. This could easily lead to not having a proper boot."

yes they're set as master and slave...i also tried booting from both dvd drives

---

### Post by wpshooter on 2007-03-21
Have you tried using the F4 key to manually choose a video mode that is compatible with your video card and monitor ?

---

### Post by phr3ak on 2007-03-21
> **wpshooter said:**
> Have you tried using the F4 key to manually choose a video mode that is compatible with your video card and monitor ?

still the same problem. it only lets me choose resolution and i've tried them all.

---

### Post by wpshooter on 2007-03-21
Have you tried the ALTERNATE (text based) version ?

---

### Post by phr3ak on 2007-03-21
is that the stripped down minimal version? Where can i find that? 
thank you for your reply!!

---

### Post by ktulu2602 on 2007-03-21
i have problems booting from the cd! the menu is loaded but when i choose to "start or install ubuntu" it start loading, the orange bar fills up and then my computer doesn't do anything. the cd-rom tray in which i have the Ubuntu CD doesn't even come out when i press the button. the keyboard doesn't work. the screen is black and that's all. i can only restart the computer. i've checked the cd and it doesn't have any problems. i've tried to start ubuntu in safe mode and again it does the same thing... what could be the problem?

---

### Post by wpshooter on 2007-03-21
No, my understanding is that is has the same feature set as the GUI (DESKTOP) version.  However, it SUPPOSED be better at doing some of the install.

---

### Post by phr3ak on 2007-03-21
> **wpshooter said:**
> No, my understanding is that is has the same feature set as the GUI (DESKTOP) version.  However, it SUPPOSED be better at doing some of the install.

i've been trying to search the ubunto site for the alternate text version you're talking about but so far i haven't found it yet. can you possible provide me with a link?

---

### Post by Lord Crow on 2007-03-21
> **wpshooter said:**
> No, my understanding is that is has the same feature set as the GUI (DESKTOP) version.  However, it SUPPOSED be better at doing some of the install.

Where is it?

---

### Post by phr3ak on 2007-03-21
is there another approach to fixing this problem versus using an alternate version since i can't find it?

---

### Post by wpshooter on 2007-03-21
try toward the bottom of this page for 6.10

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

Your can find ALTERNATE for 6.06 by doing a search on ALTERNATE.

Good luck.

---

### Post by phr3ak on 2007-03-21
> **wpshooter said:**
> try toward the bottom of this page for 6.10

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

Your can find ALTERNATE for 6.06 by doing a search on ALTERNATE.

Good luck.

I have tried it and it failed after boot menu(selecting text option and check cd defect ).....the error message is as follows:
Cannot allocate Resourse Region 0
Cannot allocate Resourse Region 1
Cannot allocate Resourse Region 3
Error while updating Region

This CD works on my other systems and cd defect is 0 (reported on my laptop). I'm starting to think its my optical drives but they're brand new.

Results so far.....system fails to get past boot menu on both official disks and alternate discs and both versions

any other suggestions?

ps....i'm thinking about trying to boot off a usb disk or a hard drive and see if that works

---

