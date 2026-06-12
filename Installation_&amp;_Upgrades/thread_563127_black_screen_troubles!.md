---
title: "black screen troubles!"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by twist2b on 2007-09-29
im getting black screen AFTER ubuntu is fully loaded... im thining this is a resolutin trouble or graphics card trouble SOOOO:
ok when i start the computer and GRUB comes up and i can press c for command line
(i want to try to fix resolution first)
ok so is there a command to corce ubuntu to open as a diffrent resolution
by the way when i started up ubuntu as a live cd it wouldnt even start unless i changed the resolution with F4 to 1280 x 800 32 i think
anyways im thinking ubuntu is getting a black screen becuase its not starting at the right resolution and having the same trouble as live cd
help? haha

---

### Post by Pumalite on 2007-09-29
Hello: Let's start with your specs.

---

### Post by twist2b on 2007-09-29
HP Pavilion tx1000z (touch screen lappy) 
AMD Turion(TM) 64 X2 Dual-Core Mobile Technology TL-64 (2.2 GHz, 512KB+512KB L2 Cache ) 
12.1" WXGA High-Definition HP BrightView Widescreen Display(1280 x 800) with Integrated Touch-screen 
(oo haha opps my resolution is diff then i remmemebered sorry)
NVIDIA(R) GeForce(R) Go 6150

---

### Post by Pumalite on 2007-09-29
We are going to have to merge both of your threads. The good news is I finally got it. I think. At the command line:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by twist2b on 2007-09-29
wait... grub? like press C when grub starts up and then type those stuffs in?

---

### Post by Pumalite on 2007-09-29
Ctrl+Alt+F1 to get a command line if you don't have one.

---

### Post by twist2b on 2007-09-29
ok im going to try that... brb

---

### Post by Pumalite on 2007-09-29
Ok.

---

### Post by twist2b on 2007-09-29
ok maybe me or you missunderstood.. i tried grubs command but it didnt understand what i was typing so i didnt get any luck there... BUT THEN when i tried to use ubuntu with ctr+alt+F1 i didnt get anything... just stayed a black screen after boot

---

### Post by Pumalite on 2007-09-29
It's when you have the black screen that you have to type Ctrl+Alt+F1.

---

### Post by twist2b on 2007-09-29
hmm i thought i did though... i guess ill try again....

---

### Post by twist2b on 2007-09-29
sorry for double post guys but ok... it wont let me open the command prompt.... is there a fualt in the download??? should i try downloading the alternet and see what happens?

with the alternet... i have the iso... put that on the cd-r and thats it right? no other files needed?

---

### Post by Pumalite on 2007-09-29
At this point, the only thing I can recommend you is start from scratch with the Alternate CD and follow these guidelines:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
(burn at 4x) Good luck.

---

### Post by twist2b on 2007-09-29
ok sweet... ill try that then.... last questions for now...
i burn it on a CD-R or CD-RW right?
also how do i get ubuntu OFF my lappy? will i have to?

---

### Post by Pumalite on 2007-09-29
CD-R. You can install ON TOP of Ubuntu.

---

### Post by twist2b on 2007-09-29
ok thank you SOOOOOOOO MUCH!!! i really appriciate your help.... ill let you know if i have any more problems after install

---

### Post by Pumalite on 2007-09-29
You are welcome. Good luck!

---

