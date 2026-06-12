---
title: "Ubuntu 9.10  clean install problem"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by tzole on 2009-12-08
Hi

I have  an old  Desktop ( Pentium 4  2,8Ghz) with an old Philips  170 s4 monitor  and GeForce 7600 gs graphic card.
  I tried a clean  installation of the 9.10 ubuntu(form a liveCD).After  pressing "install Ubuntu" (in the menu where it askes, wheather you want to "test memory" , "check disk for defects" , "try ubuntu without any change to your computer" …) it took  2 minutes and then the follow message showed up :
   
  CANNOT DISPLAY THIS VIDEO MODE ,CHANGE COMPUTER DISPLAY INPUT TO 1280X1024@60HZ
   
  In other post, some suggest to change  resolution from the /etc/X11/xorg.conf but the file is empty .I am not sure what the problem is, I imagine that my monitor  has problem with the resolution(i suppose i have to install ubuntu in a lowwer graphic mode that my monitor can deal with that) but i  have no idea from where can i change it .Because i have no graphics , only the terminal when i press ctrl+alt+F1,any help?

---

### Post by u.b.u.n.t.u on 2009-12-08
Hi and welcome to Ubuntu forum. The Philips 170 s4, is that the 17" or 15" CRT?

When installing Ubuntu 9.10 look for the option to change video resolution and choose something like 800x600 with 16 bit.

As for the xorg.conf, such will only exist if you have installed proprietary drivers or specifically created such.

---

### Post by tzole on 2009-12-08
it is the 17''(not the crt)

I m not sure where to look for that option, to change video resolution.I saw that in some past destros when someone press f4 is able to change resolution but in that destro when i choose f4(Modes)  i got a menu with the options : Normal,Safe graphics mode,use driver update disc,OEM install (for manufactures) but none of this options made any difference.

---

### Post by u.b.u.n.t.u on 2009-12-08
I only have an ISO of Ubuntu 9.10 and when I went to check, I was only presented with the uninstall option.

However checking the screenshots at the wubi site, I notice a button with the word "accessibility". Is that an option to define display settings?

[http://wubi-installer.org/screenshots.php](http://wubi-installer.org/screenshots.php)

---

### Post by tzole on 2009-12-08
F5  (Accessibility) comes with the following menu : None,High Constrast, Magnifier , Screen Reader , Braille Terminal,Keyboard Modifiiers ,on -screen keyboard but no display option unfortunately

---

### Post by u.b.u.n.t.u on 2009-12-08
Do you have another monitor to test?

---

### Post by tzole on 2009-12-08
no :(

---

### Post by u.b.u.n.t.u on 2009-12-08
Are you able to test a live CD version of Ubuntu 9.04? If you have one lying around or download if that isn't a huge deal.

What is the current operating system on the HDD?

---

### Post by tzole on 2009-12-08
I will buy a cd tomorrow for the 9.04, the current os in the hdd is the windows  XP black edition.

---

### Post by u.b.u.n.t.u on 2009-12-08
> **tzole said:**
> windows  XP black edition.

Yeah ok there! ;)

The 9.04 may help determine if it is the hardware or 9.10.

---

### Post by thenewcrowd on 2010-01-05
I am having the same problem, different computer, same class video card. 9.04 was installed, "partial upgrade" messed it up, now with network manager all garbled i am just sayin to heck with it and doing a fresh install but with any video mode the computer comes up with the same "check display settings" message. 9.04 works well so if you want to use that that's fine.

---

