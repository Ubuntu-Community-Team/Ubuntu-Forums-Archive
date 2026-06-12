---
title: "&quot;Ack!  Something bad has happened.&quot;"
date: 2005-02-11
forum: Installation &amp; Upgrades
---

### Post by wndozdefector on 2005-02-11
Long story short. After a visit to windows update, I now have to "activate my product." What followed was an episode where I became slightly enraged at being locked out of my own computer. 

Did some homework online and liked Ubuntu because it's totally free and one install CD comes with preinstalled packages. Wow.

Full disclosure. I'm a total linux newbie.

Downloaded and burned ISO onto CD. No partitions, did a clean install of Ubuntu onto my HP Brio, 733mhz, .6gb RAM, 20gb HD, onboard video, with network card. 

Initial installation proceeded with no problems until I got to the downloading portion of the install. The computer asked to reinsert the install cd to /cdrom/ and then what followed was: 
"mdprob: FATAL: Error inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko): Operation not permitted"
..and ".../hotplug/pciehp.ko instead of .../hotplug/shpchp.ko)"

Then many many lines of I/O error at hdc. blocks 104570, 104571, 104572, etc

Many dependency errors when installing packages. 

Finally I noticed... "Ack! Something bas has happened." 

After reboot, the screen says "GDM: Xserver not found: /usr/x11r6/bin/x :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7"

On this other computer, I've printed examples of debian linux commands hoping to learn something. 

Does anyone know what the heck happened?

---

### Post by rmjokers on 2005-02-11
One possibility is that you got a bad burn of the install CD.  The "FATAL" errors you mentioned are actually normal.  I get them on my screen when I boot up my laptop too.  Since /dev/hdc is probably your cdrom drive you got errors after you inserted the CD, I am guessing it is part of the problem.  Try burning doing a checksum on your install .iso and then burn a new copy of the CD and see if that helps.

---

### Post by jdong on 2005-02-11
Your CD is damaged or otherwise unreadable. :(

---

### Post by wndozdefector on 2005-02-11
UPDATE: I burnt another one with hoary array 4 (the first one was warty) and the installation went much better... however, on reboot the X server refused to load. I get an error message displaying the x window system version 6.8.1.902.

Thanks for the suggestions to burn another CD. It solved the FATAL stuff and got me much closer to finally defecting windows. I can see I have a lot of learning to do.  \\:D/

---

