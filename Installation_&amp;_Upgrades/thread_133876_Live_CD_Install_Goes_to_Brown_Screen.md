---
title: "Live CD Install Goes to Brown Screen"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by jonmac on 2006-02-20
I am very new with linux and thank you in advance for your support and patience.  My goal is to dual boot with Linux and windows, I obtained live cd's and have run into a problem.  The live cd goes through all of the checklists, checking for hardware, keyboard etc.  It then goes to a black screen with the ubuntu logo and a checklist pops up and as it runs through items are listed as "ok", the last item on the list is "starting gnome display manager."  The screen goes blank for a few seconds and then a brown screen pops up with a jumbled rectangle in the middle of the screen.  I can make out "Ubuntu" in the rectangle, and "windon manager" on the bottom of the rectangle in small font.  This is where the install freezes, I can still move the mouse but nothing happens.  My machine has the following specs:

AMD Athlon X2 4400+
4GB RAM (4x 1GB)
ASUS A8N-SLI Deluxe
nVidia GEforce 7800 GT
2x74GB WD Raptor in RAID 0
80GB WD

Once I have the live cd working I plan on trying to dual boot with Ubuntu on the 80GB disk and XP on the raid array.  Any information or direction you can give will be greatly appreciated.  Thank you in advance.

Cheers

---

### Post by Coelocanth on 2006-02-20
I'm not sure how to fix it so the live CD will work, but I think the problem is the video card. I installed Ubuntu from an ISO I DLed and got nothing but a jumbled screen upon booting. I have a GeForce 6800 GS in my system and it turned out the problem was the drivers. The proper drivers for my card are not included with the install, so the only way I could manage to see anything on the screen was by choosing the vesa drivers instead of the nv drivers and then finding the proper nVidia drivers and installing them after (which also involved editing the xorg.conf file).

I figure your card is the problem. Like I say though, I don't know if you can fix it for the live CD (I'm not all that tech savvy...)

---

### Post by jonmac on 2006-02-21
Thank you for the reply, I had guessed that this was the problem by reading other threads.  It seems that the way to fix it is to hit ctrl+alt+F1 and then type in "sudo nano /etc/X11/xorg.conf" and change ther driver from nv to vesa.  The problem with that is that when I hit ctrl+alt+F1 nothing happens, no terminal or anything.  Do I need to skip the live cd and go with the install for this to work?  Thank you in advance for the help.

Cheers,
Jon

---

### Post by tenshu on 2006-02-21
i think it is the NV driver too

How your raid 0 is recognize?

---

### Post by Schmots on 2006-02-21
maybe teminal one isn't up.. try ctrl+alt+f2 or f3 or f4 even

---

### Post by jonmac on 2006-02-21
I havent worried about how the raid 0 is recognized yet, I figure that booting off the live install cd would take that problem out of the equation, is this true or false?  I didnt know I could access other terminals by hitting F1, F2, F3..., I will try that and see if it works.  Thank you both for your replies.

Cheers,
Jon

---

### Post by jonmac on 2006-02-21
Anybody have any info on how to go about switching the driver from nv to vesa?

Gracias,
Jon

---

### Post by claubuntu on 2006-02-21
The Problem is Vga Resolution default into /etc/X11/xorg.conf

do 

*pres keys alt+F2 for login

sudo vi /etc/X11/xorg.conf

*press key i for entrance mode of insertion

find the line

Section "Screen"

del all resolutions "1280X1024"

*press key Esc for exit mode of insertion

*press keys q+w for quit and write

*press keys ctrl+alt+backs for reset Xserver

ok your grafic login will be back...

---

### Post by jonmac on 2006-02-21
Thank you very much for the help!  I was able to get the live cd up and running beautifully.  My next step is to set up a dual boot on my system, I hear this can be tricky with a RAID 0 array so cross your fingers for me.  Anybody know if Ubuntu is compatible with dial up modems?

Gracias,
Jon

---

### Post by HS_Hammer on 2006-04-13
Hmmm...ran into this same problem is seems.  Just downloaded the Live CD (Ubuntu 5.1 for AMD64).  Here's what I have:

AMD Athlon 64 3700+
2GB RAM (2x 1GB)
ASUS A8N32-SLI Deluxe
nVidia GEforce 7800 GT OC


Getting the exact same symptoms as the OP (including the startup music!), but except that I get that brown screen with a tiny bit rectangle, where I can't make out anything...

...so, the solution where you go Alt-F2 or whatever doesn't help at all (tried it, hoping that Alt-F2 would bring it to a full terminal window...but that didn't work).

Any ideas?

Thx

---

