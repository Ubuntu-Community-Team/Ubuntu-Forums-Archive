---
title: "blank screen blinking cursor with live boot CD"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by cedavis8 on 2008-03-20
i put in the live CD to boot from it so i can install Ubuntu on my newly partitioned drive. I click start or install ubuntu and it looks as though it will start up. it then loads for about 5 minutes and then shows a blank screen with a blinking cursor.......

Oh right, when i press ctrl + alt + F1 it shows Loading please wait... and i can type (though it does nothing) ctrl + alt + F7 does nothing...help please...

---

### Post by Pumalite on 2008-03-20
Post your specs.

---

### Post by cedavis8 on 2008-03-20
I have a Dell, i don't know what model but i do know i've had it for about 4 years. I have Windows XP Home Edition right now.

I have an Intel 82845G/GL/GE/PE/GV Graphics Controller (my geforce MX 4000 graphics card doesnt work with ubuntu)
I have a DELL E153FPT Monitor
I have an Intel 82801AB AC'97 Audio Controller
1 GB RAM
a 111 GB Harddrive with 3 partitions (one accidental)
An Intel Celeron with 2.39 GHz processing speed and 2.4 GHz CPU

---

### Post by Pumalite on 2008-03-20
Install with the Alternate CD. Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'

---

### Post by cedavis8 on 2008-03-20
how do i install it with that once i'm in it? or does it tell you? cause i have to install it on a partition i made in windows that i have and i know how with the graphical interface...

---

### Post by Pumalite on 2008-03-20
You might want to take a look at this excellent guide:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by cedavis8 on 2008-03-20
hmmm doesn't really fit what i want to do...i decided to go with kubuntu because it looked like really what i wanted and that site doesnt have how to install onto an already partitioned drive.

---

### Post by Pumalite on 2008-03-20
Boot your Live CD and from the Terminal, post:
sudo fdisk -lu

---

### Post by cedavis8 on 2008-03-21
i can't boot from a live CD...oh right i tried to install from the alternate CD but it would stop randomly at different spots for no reason...

---

### Post by Pumalite on 2008-03-21
Maybe a bad burn. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on the iso, burn at 4x or less on CD-R, check CD integrity after burn and before install. Clean the lens in your burner, just in case.

---

### Post by cedavis8 on 2008-03-21
thanks man i'll try that

---

### Post by Pumalite on 2008-03-21
Good luck.

---

