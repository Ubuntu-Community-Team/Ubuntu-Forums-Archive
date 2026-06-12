---
title: "Packet Tracer problem"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by dimago on 2011-07-29
Hello All...

Im using ubuntu 11.04 and I want to use Cisco Packet Tracer.

I followed a tutorial, and its said to me to comment this line:

#export LD_LIBRARY_PATH=$PTDIR/lib inside the /usr/local/PacketTracer5/packettracer

and Install some libs, like this:

libqtwebkit2.2-cil libqt4-script libqt4-qt3support libqt4-sql

this work is to show the fonts inside the packet tracer with a best visual...

My problems are as follows:

 - If I save the project, when I click in the project.ptk, it dont open, It open like a new file, so I need to click in Open, inside the packet tracer and choose the file project.ptk (version 5.2 and 5.3)

 - If I try to open a Generic Computer, its closes my Packet Tracer. (in version 5.3)

 - In the version 5.2, I lost my work. I had finished my work. I saved and close the program. After, I open the program, and when I clicked in Close, it ask to me to Save the File or Not or Cancel. I choose Yes, save the file. After this, my work had disappear. The file had 0kb. (in version 5.2)

Its my problems, if anyone can help me :)
Thansk anyway,

Diego

---

### Post by tillerdemon on 2011-07-29
Had the same problem in 10.10, seems it's a issue with exporting the line out. I believe cisco has fixed teh issue with the fonts and you no longer need to do the fix. Did you install at root user level?

---

### Post by dimago on 2011-07-29
> **tillerdemon said:**
> Had the same problem in 10.10, seems it's a issue with exporting the line out. I believe cisco has fixed teh issue with the fonts and you no longer need to do the fix. Did you install at root user level?


Hey,

Yes, I downloaded the .bin from the cisco netacad.

chmod +x file.bin

When I start the program, Im using a regular user.
I tryed with a root user but the problem continues.

Another ideia?

---

### Post by dimago on 2011-07-29
> **dimago said:**
> Hey,

Yes, I downloaded the .bin from the cisco netacad.

chmod +x file.bin

When I start the program, Im using a regular user.
I tryed with a root user but the problem continues.

Another ideia?


Its works now. :) 
But, when I try to load a saved file, packet tracer opens like a new file, I need to click in Open (on the menu) and select the file.

Anyway to fix this?

Thanks,

Diego

---

