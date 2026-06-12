---
title: "Kubuntu or ubuntu wont boot (no grub)"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by Dark_Sabre on 2008-04-06
i have tried to install both ubuntu and kubuntu 7.04 (a bit old i know) and neither of these operating systems will show the grub when i start my pc. i have tried reinstalling the grub itself via the live cd and it still wont work.

this is my pc's specs:

Processor: 	
Intel(R) Pentium(R) 4 CPU 3.00GHz (2 CPUs) (i dont know why)
Memory: 	
1024MB RAM
Hard Drive: 	
164 GB (and a 20 gb one with kubuntu installed obviously not working)
Video Card: 	
RADEON 9250
Monitor: 	
Plug and Play Monitor
Sound Card: 	
Realtek AC97 Audio
Speakers/Headphones: 	
Nicole Multimedea Speaker System
Keyboard: 	
USB Root Hub (wireless cyber)
Mouse: 	
USB Root Hub (wireless cyber)
Operating System: 	
Windows XP Professional (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.070227-2254)

can anyone please help me? :confused:

---

### Post by confused57 on 2008-04-06
Open a terminal(or konsole if Kubuntu), post the output of:
```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list

Have you tried changing the boot order of the hard drives in bios?

---

### Post by benstoked on 2008-04-06
I had a similar issue.
my config:
athalon 64 x2 4000+
2gb ram.
sata 320 gb (OS Drive)
IDE 160gb (my files)
IDE dvd+/-rw
hardy beta
xp pro
320 gb split in half for each os

I have one ide channel, so both my dvd and 160 gb are on it.
when booting from the live cd to install, it calls the 160 hd0 and the sata hd1
so when grub was written, it wrote everything on "hd0"
my bios is set to boot the sata, not the ide hd, so it does not see grub.

possible solution 1:
change bios to boot ide hd( didnt try, was late, and i was ready for bed)

my fix:
put in the live cd, and boot from it
follow the instructions here:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
until you get to the "setup hdx"
change to ```
 setup hd1
```

open up nautulus(file browser) and navigate to the hard drives /boot/grub
edit the menu.lst, swapping hd0 for hd1 and vice versa.
also under the wiindows entry, remove```
map		(hd0) (hd1)
map		(hd1) (hd0)
```
making sure there is no empty line between makeactive and chanloader commands

my system works "fine...":lolflag:

---

### Post by Dark_Sabre on 2008-04-07
for confused:it said it couldnt find it but when i went 

sudo grub

find /boot/grub/menu.lst 
it said it was on hd0.

ty if you can get it to work if benstoked doesnt work

for benstoked: ty i shall try that.

---

