---
title: "help installing GeForce linux kernel"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by twist2b on 2007-09-29
well im a totall newb so i dont know how to download it.... oo and by the way i have to install it on windows becuase i get a black screen when ubuntu fully loads.... so its not reading the graphics card to project anything...
so im such a newb that any step by step instructions would be nice

i cant figure it out becuase its a run file and the guide doesnt help that GeForce made

---

### Post by Pumalite on 2007-09-29
Let's start by you giving us your specs.

---

### Post by twist2b on 2007-09-29
HP Pavilion tx1000z  (touch screen lappy) 
AMD Turion(TM) 64 X2 Dual-Core Mobile Technology TL-64 (2.2 GHz, 512KB+512KB L2 Cache ) 
12.1" WXGA High-Definition HP BrightView Widescreen Display(1280 x 800) with Integrated Touch-screen 
(oo haha opps my resolution is diff then i remmemebered sorry)
NVIDIA(R) GeForce(R) Go 6150 
anything else you need?

---

### Post by Pumalite on 2007-09-29
You definitely need the Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign 'Start Download'
And follow these guidelines:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

(We'll fix the problem of your display later)

---

### Post by twist2b on 2007-09-29
so the one that was sent to me was not made for my computer???? its 7.04
this is really good to know... can you just explain why i need alternate?

---

### Post by Pumalite on 2007-09-29
To avoid graphical and other potential hardware problems. You could try some boot parameters on yout Live CD. Hit F6 at boot and add noapic at the end of the line. If not that you could try this:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

I think the Alternate is a better option though.

---

### Post by twist2b on 2007-09-29
ok wait one sec though i already installed ubuntu can i try F6 now that its installed and try that? like will it work ON the drive?

also if this doesnt work ill try alternate.... thanks a ton though this is good to know

---

### Post by Pumalite on 2007-09-29
Wait a sec..if you already installed Ubuntu, you better explain to me better where you are stuck.

---

### Post by twist2b on 2007-09-29
ok sorry...  heres what happens:
now ive explained that the live cd wont even start withought resolution change with F4 but heres the situation
now that its installed grub comes up yada yada
then when i press enter on the ubuntu kernel it loads FULLY everythings fine... but then instead of moving on it black screens.... i think its a resolution error becuase the live cd wont run ubuntu uless i change my resolution either

---

### Post by Pumalite on 2007-09-29
I posted the (hopeful) solution in your other thread. Let's stop this one and stick to the other one only.

---

