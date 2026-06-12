---
title: "I can't get the xubuntu live cd to load"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by Mcmoe on 2007-08-11
I'm trying to install xubuntu 6.06 on an old IBM thinkpad. i put the live cd in and it takes me to the menu thing where i hit "start or install". it starts to boot ok, but freezes up when trying to mount the root file system.

I then get a message that states - /bin/sh: can't accesstty; job control turned off.

the same cd works on anouther computer.

what is the problem?

---

### Post by Pumalite on 2007-08-11
This is a common problem with no one answer. There is an extensive thread in this forum that might help you. Try Search.

---

### Post by Mcmoe on 2007-08-11
to be honest i really don't know what i'm doing. 

i just tried using the alternate cd and it started ok, but now i have an error message that states that i need to load additional cd-rom drivers from a driver floppy.

where exactly wood I get those drivers?

---

### Post by Mcmoe on 2007-08-11
I can't spell either :)

---

### Post by Pumalite on 2007-08-11
Why don't you post your specs and see if I can help you better.

---

### Post by Mcmoe on 2007-08-11
Thinkpad Laptop Type 2611 i series
366 mhz Pentium II Processor Celeron
128MB of RAM
roughly 4 GB hardrive

---

### Post by Pumalite on 2007-08-11
128 MB RAM or less> Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by Mcmoe on 2007-08-13
Hey, that worked. thank you soooo much. :)

one more thing though.

everything loaded fine, but for some reason i can't mount audio cd's

---

### Post by Pumalite on 2007-08-13
This has to be a BIOS problem. Enter the BIOS and make sure it is recognized by it. in the meantime post the results of 'lspci' Also go into your /dev folder and see if you have a device for cdrom

---

### Post by Mcmoe on 2007-08-13
I have a folder for the cdrom but it's not in the dev folder. 

i think my cd drive is recognized cause i can look at pictures and stuff that are saved on a disk. i just think it might just be the format of and audio cd or something, but then again i'm not a genius when it comes to this.

right now i don't have any way to hook my computer up to the internet. is there some way i can load updates onto a disc then load them onto my computer?

one more question for you... i hope. i've been looking at nic cards for my computer. are there certain ones that already have the drivers installed in the os.

---

### Post by Pumalite on 2007-08-13
You should start a new thread in the Sub-Forum 'Networking'. Better and faster answers.

---

