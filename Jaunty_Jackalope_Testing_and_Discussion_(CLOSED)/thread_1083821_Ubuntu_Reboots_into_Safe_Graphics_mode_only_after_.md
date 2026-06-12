---
title: "Ubuntu Reboots into Safe Graphics mode only after upgrade"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by homeriq5 on 2009-03-01
Hi all, 

I've recently tried to upgrade from intrepid to jaunty on my sony vaio FW290 laptop and am experiencing some annoying problems with the graphics after the upgrade.  Every time I log in, it says that it cannot detect my graphics device and settings, says that it will log in on low graphics mode, then it cannot detect which screen to use because :0 is busy, then it boots into the desktop and I have to use gedit to mess with xorg.conf.  I've tried to install ati catalyst control 9.2 to install the latest fglrx driver but that doesnt help either, it says it cant detect the driver after I try to open it.  I also tried to change the graphics device to ati and radeon hd, but that doesnt change anything either.  Can anyone help me?  I've been using ubuntu to run some bioinformatics applications lately, but now I guess I'll to stick to windows 7 beta on my other partition :(

---

### Post by homeriq5 on 2009-03-01
Oh, I am also using a ATI Radeon HD 3650 Series graphics card and 64-bit ubuntu intrepid

---

### Post by ptn107 on 2009-03-01
I've had the same problem with 9.04 alpha 5 x86_64.  My solution for now is to just keep clicking through the prompts and eventually it will ask to start a display on :1, just say yes and everything will look fine.  Though, you will have to do this on every restart.  I have scanned through my xorg.conf files from before and after the upgrade that caused the problem, from what I see both files are identical so the problem must be something else with X.

---

### Post by homeriq5 on 2009-03-01
Hmm, well I tried that but the screen is the wrong resolution when I log in (still in safe mode I guess).  I guess I'll just have to wait for an update to xorg?  This is kinda bad because its going to make my work a lot more difficult since I cant see the entire desktop at a time :(.  I upgraded in previous versions to late alphas and never encountered serious problems like this before :(

---

