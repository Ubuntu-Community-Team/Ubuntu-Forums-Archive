---
title: "new installation fails to boot"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by someguyonthestreet on 2007-02-14
I've  been working  at  this computer for perhaps a day now. I  tried to install, kububtu with the live cd. And it runs for a little but it  doesn't get  to the desktop and it says 

mount: function not enabled

fsck 1.1 (29 may 2007)

and  then the font changes and then it hangs.

So i tried xubuntu, same problem, then mandriva, same problem, then i tried the alternate  installl cd for xubuntu. It installls fine. But  when you go to boot it up, the little bar  fills, then it blank screens, I tried the alternate for ububtu same problem. Please help.

Te new installation fails to boot. That's the problem at hand now.

specs: 733mhz pentium 3
300mg pc133 ram
i815 chipset

---

### Post by IgnorantGuru on 2007-02-14
It sounds like a video problem.  When the bar fills up the X server tries to start.  You can try pressing Ctrl-Alt-F1 and see if it takes you to a console (text) screen.  Also try Ctrl-Alt-Backspace (which kills the X server).

You might do a google search for "ubuntu install blank screen" and your video card make and model - see what others are talking about.

If you make it to a console, type 
sudo dpkg-reconfigure xserver-xorg

That will reconfigure the x-server.  Then reboot.

---

### Post by someguyonthestreet on 2007-02-14
ctrl alt  f1 goes through some stuff then black screens. cntrl alt backspace doesn't work either.  i had a look at my video card, and it's plugged into anoter card in another pci slot. I'm pretty sure  they don't make  them like that anymore. that's prabably  it.it says blaze 3d ultimate on it. But i can't see te  serial number. 

edit:  i have  a similarmachine with the same graphics card, on which i got ubuntu to work. I think  i'll just move  the faster parts to that machine. But the motivation to get it to work on mine, is the learning process

---

### Post by someguyonthestreet on 2007-02-15
Okay, i was using a trident 3dimage975 graphics card. (jaton 3d ultimate).. I checked and it seems to be supported by linux.  It's a vga graphics card. I wonder if that it.  and the card itself was plugged into a tv tuner card. The phillips bzt k u09 276. I'm still really eager to fix this computer! Someone plz respond.

Update: got it working  by pluggging  it into  that motherboard. was a ggraphics card issue. i'm wondering  how you acces te  console from the desktop.  i'd like to  try to  get the graphics card working.

---

