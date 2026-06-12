---
title: "Ubuntu install stops in the middle.."
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by StevenEpic on 2007-08-15
i finally set my mind straight and decided to install ubuntu. i was following every direction it was giving me. after the network configuration stage, it flashed this on the screen: [COLOR="Red"]Detecting disks and other hardware[/COLOR] then after the red bar filled, the next stage didnt show. i believe, the partition stage.

i checkedd to see if the cd was corrupt, but it said it was valid.

anyone know whats going on?:confused:

---

### Post by ddrichardson on 2007-08-15
Need to know more about your machine - memory and drive configuration particularly.

---

### Post by StevenEpic on 2007-08-15
its a pretty down machine :D

149 GB hard drive
Intel Pentuim 4 CPU 2.80GHz
3.11 GHz, 1.62 GB of RAM

---

### Post by Pumalite on 2007-08-15
Try Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by StevenEpic on 2007-08-15
THAT is the one i downloaded and use. im gonna try the desktop one. thanks anyways :]

---

### Post by jamesjtucker on 2007-08-15
I had this issue once, it turned out to be bad RAM. Try the memtest on the install cd and see what happens.

---

### Post by Pumalite on 2007-08-15
You have too little memory for the desktop. Better stick to Zenwalk or Damn Small Linux if you couldn't stick Xubuntu in that machine.

---

### Post by ddrichardson on 2007-08-15
He has 1.62 Gb of RAM - its not being short of RAM

---

### Post by Pumalite on 2007-08-15
You are right. I mistook the hard drive for the memory.

---

### Post by ddrichardson on 2007-08-15
How're the drives configured - is it ide, sata, raid?

---

### Post by StevenEpic on 2007-08-15
i believe its ide O.o

---

### Post by StevenEpic on 2007-08-15
i think the partitioner is not detecting the hard drive. i am currently in the destop live cd and i started the installation, and the partitioner hangs at 46%

NEVERMIND.

the partman started alright. does it install the same from the live cd than the alternate? yes right? :]

---

### Post by ddrichardson on 2007-08-15
You don't have any USB devices plugged in do you? Like printers with media card slots?

---

### Post by StevenEpic on 2007-08-15
my keyboeard and mouse are USB ?

ok im in the partitioner. but i get this [in the screen]("http://i17.tinypic.com/6fretg7.png"). and i know my harddrive has 85 GB of free space. whats going on?

---

### Post by ddrichardson on 2007-08-15
Its normal. It doesn't mean free space on that partition - Windows almost always leaves a few MB unallocated when it creates a partition.

---

### Post by StevenEpic on 2007-08-15
so how do i resixe that partition?

---

### Post by ddrichardson on 2007-08-15
Backup first. Then right click on the partition to resize - the large one and choose resize.

---

### Post by StevenEpic on 2007-08-15
it is asking in byte format. i want it to be 80 gigabytes. how much is that?

---

