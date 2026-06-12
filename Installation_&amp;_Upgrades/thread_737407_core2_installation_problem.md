---
title: "core2 installation problem"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by malluda on 2008-03-27
hi everyone!

i have a problem with ubuntu installation in a centrino dual core processor.
i tried to install 7.10 desktop edition (the first choice) but installation does not procced. 

do you know what edition to install?

---

### Post by lswest on 2008-03-27
try starting it in safe graphics mode (second option on the boot list)

---

### Post by malluda on 2008-03-27
ok i will try it.

i forgot to tell that i chose 7.10 for Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM) choice.

i

---

### Post by stchman on 2008-03-27
> **malluda said:**
> hi everyone!

i have a problem with ubuntu installation in a centrino dual core processor.
i tried to install 7.10 desktop edition (the first choice) but installation does not procced. 

do you know what edition to install?

It's highly unlikely that the processor is the problem as Ubuntu supports SMP.  It is probably your video card.  Try the safe graphics mode.  What type of video card  does your system have?

---

### Post by malluda on 2008-03-27
yes some video characteristics during the installation fail.

i have ATI mobility Radeon X2300. will ubuntu recognize it in safe graphics mode installation?

Thanks!

---

### Post by lswest on 2008-03-27
in safe graphics mode Ubuntu runs a generic driver (called "vesa") which gives you basic functionality with pretty much any card, and then for 3d acceleration and such, you'd need to install the propriety ATI drivers, but it should work.

---

### Post by malluda on 2008-03-27
someone suggested that alternate edition should. what's your opinion?

Thanks anyway!

---

### Post by malluda on 2008-03-28
i tried to install ubuntu 7.10 in safe graphics mode but nothing. video card is not recognized and installation does not proceed in black view.

what can i do now?

my graphics card is ATI Radeon X2300

---

### Post by clarknova on 2008-03-28
Does your motherboard have on-board graphics? Can you try another graphics card? If you can complete the install using another graphics card then you may still be able to install and enable the proprietary ATI driver (fglrx), change back to the ATI card, and run successfully.

Try another video card or on-board video for the install and report back.

db

---

### Post by malluda on 2008-03-28
i am trying to install ubuntu in a sony vaio vgn-cr laptop. not in a desktop pc

---

### Post by clarknova on 2008-03-28
Right, you did say mobility. Sorry.

I would suggest trying another version. You may have better luck with 8.04 beta, which is freshly out.

db

---

### Post by malluda on 2008-03-28
i am afraid to use beta versions. what about alternate?

---

### Post by malluda on 2008-03-28
if i install Kubuntu or Xubuntu, do you think that overcome the problem with the graphics card?
what other diferences are there except of KDE?

---

### Post by lswest on 2008-03-28
Sorry for the absence, i was asleep XD just woke up.  What the alternate CD is is a text-based install, which might seem a bit more difficult to do, but ultimately it will install the system, but definately require some command-line help to get the graphic card up and running, since even safe graphics mode couldn't boot.  And lastly, Hardy is a viable option, sure, it's in Beta stages now, but i run it on my laptop and i find it has improved immensely.  If nothing else works, give it a try.

Also, XFCE and KDE probably won't affect the graphics situation much, they all use the same drivers.  Ultimately though they all use the base ubuntu software, and just have a different user interface.

---

### Post by malluda on 2008-03-28
thank you lswest!!

i will install 8.04, i hope not having troubles with the beta version

---

### Post by lswest on 2008-03-28
no problem, always happy to help :)

---

### Post by clarknova on 2008-03-29
In another 4 weeks 8.04 will no longer be beta. If you succeed with the install just keep your system up to date and you won't be running beta in another month.

db

---

