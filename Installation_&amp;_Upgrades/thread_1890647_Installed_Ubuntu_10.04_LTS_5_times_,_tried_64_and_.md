---
title: "Installed Ubuntu 10.04 LTS 5 times , tried 64 and 32 tried cd and usb..."
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by blazerboy777 on 2011-12-03
Im getting a messed up install im assuming on my system.

System specs are
i7 2600k
8 gb ddr3 1600 mhz ram
1tb samsung f3 spinpoint hard drive
2x GTX 470
 
Other specs seem unapplicable

Ok so I get in install everything good to go, says needs to restart, I restart and boom nothing. I get a blinking underscore and thats it, its happened 5 times now to me, aka i tried installing in different ways and the same thing happends every time.

I cant alt ctrl f1 to terminal nothing it just fails to boot Im assuming. Any help would be most welcome. Iv tried the x86 and x64 bit architechtures for this tried both on cds dvds and usb flash drives. Installs everytime perfectly (so it seems) just doesnt do the major part of it....boot up lol

---

### Post by collisionystm on 2011-12-03
its your video cards. 

you need to boot with nomodeset and install the driver

reboot your computer, keep tapping the UP arrow key to stop the grub menu
press E to edit the line

where it says SPLASH, put 

nomodeset next to it

hit F10? I think to boot. It tells you what to press

it should load up. then download the nvidia drivers and install

---

### Post by blazerboy777 on 2011-12-04
Pressing up and thats not doing anything, i dont think its even getting to the grub menu

---

### Post by blazerboy777 on 2011-12-04
Iv tried holding shift while boot iv tried everything its just not working i dont know why. Its not hitting grub or anything, after bios is done loading it just shows a black screen with a blinking cursor, i thought maybe it was bugged and it would continue later, so I left it for like 45 minutes while I got something to eat, nope same thing.

---

