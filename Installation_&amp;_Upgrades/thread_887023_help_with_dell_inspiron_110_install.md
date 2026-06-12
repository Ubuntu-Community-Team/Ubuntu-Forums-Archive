---
title: "help with dell inspiron 110 install"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by cpt blue on 2008-08-11
hi
first time poster on here so go easy

i had a dell inspiron1100 that i gave to my son whilst at uni
he has since bought a new one and gave me the 1100 back, when i got it back i thought great i would have a laptop to roam around with but my joy was short lived when i discovered that my son has filled it with trojans virus's etc
as he has lost the install cds i didnt know how to clean it up, then a friend told me to install linux and it was a snap to do

somehow ive managed to mess it up ;-)

so far i have done this

i wanted to have a duel boot incase i had to use some MS software so i used GParted to partition the drive, GParted would load except from the memory option once i got it going i partitioned the drive, but in my hast and not reading the popups correctly ive managed to delete the whole drive and create 2 partitions in fat 32

when i inserted the live cd of ubuntu 8.0.4 it loaded up installer and i clicked on install ubuntu it then took 10 mins as a black screen before it went thru some command line checks, it then got stuck into some error "SQUASHFS" CHECKING BLOCK it repeated this for 30 mins or so before just going to a black screen with a cursor _ line. i didnt try any commands as my knowledge is limited and my computers of choice are macs

so now im left with a dell 1100 with no os on it partitioned in half in fat32
can anyone help i would really like to get it going with linux i dont want to chuck it away, it seems such a waste and from what ive seen of ubuntu with screenshots looks great

please any help and if you could keep it layman's that would be welcome

thanks

---

### Post by reebnek on 2008-08-19
Check out [**[COLOR="Blue"]Oilgeek's posting[/COLOR]**]("http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/dell-inspiron-1100-which-distro-604288/").
I avoided step 7, and 8.04 worked for me.

STEPS:
  1 upgrade the 1100 bios to A32
  2 change the video shared memory in the bios from 1 to 8 meg
  3 do Ubuntu install in "video safe mode" - will use VESA driver
  4 perform all updated and patches
  5 add the video card info found in this reply in /etc/X11/xorg.conf
  6 add the screen info found in this reply in /etc/X11/xorg.conf
  7 sudo aptitude install 915resolution
  8 reboot and rock out with Ubuntu!

---

### Post by jbrax on 2008-10-20
If you get blank screen after every other boot, add this: 
**9. Change splash to nosplash, line 89 in /boot/grub/menu.lst** 
This changes the default so that every new kernel will get "nosplash" attribute. If you have already updated the kernel change "splash" to "nosplash" in every existing kernel line too. 

For more detals see my comment at [http://ubuntuforums.org/showthread.php?t=819541](http://ubuntuforums.org/showthread.php?t=819541)

---

