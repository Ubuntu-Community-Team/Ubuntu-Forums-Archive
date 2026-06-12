---
title: "Problems : 3 different problems"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by ^NeoPhyt3^ on 2008-10-14
I have been trying to install ubuntu 8.04 for 2 days now.I have searched this forum for solutions but i am unable to find any.I cant get through the installer.I am facing following problems.

My PC Config is :

AMD Athlon 2000Mhz
1.43 GB RAM.MSI K8NE Motherboard.
120 GB HDD     : Current OS : WinXP 

1.During My First Attempt i was facing the problem of I/O Error.I followed the advice on f0 and Burned a new CD at 8x.I got through this problem.
2. When installer reaches to a point where ubuntu is written on top and a progress bar is present and bar is moving right and left.It gives an I/O Buffer error.I again searched the forums and followed following suggestions but nothing seems to work :
a. adding pci=nomsi in Advanced Boot Setup 
b.adding irqpoll in Advanced Boot Setup
c.I looked up my BIOS and i dont have any SATA settings.Hence i cannot change from IDE to RAID.



3. Please also suggest a Partition Mechanism for Me.I have 4 drives of 30 GB each with FAT32 file system. 1 Drive has Win XP. Please tell me how to create Partitions in my drive using GParted.I need a New Drive Structure.

Hope you guys help Me.   :(

---

### Post by ^NeoPhyt3^ on 2008-10-14
Also I have read at lots of places in the forum that i am typing this during Live Install and This works ............     

I need to ask how can you guys access the net and this forum when the Live CD is running ????

---

### Post by forger on 2008-10-14
Perhaps your cd/dvd drive isn't working properly.. they usually tend to break after a couple of years (personal experience)
I would suggest to try with another cd/dvd drive, either buy a new one or borrow from a friend, just to see if this is the case :)

In my case, my old dvd-rw drive couldn't read a bootable disc during boot-up, but burning and reading cds were functioning normally in an operating system (windows or linux)

---

### Post by ^NeoPhyt3^ on 2008-10-14
I know my c.d. drive is working pretty well because out of lots of attempts to install ubuntu i got lucky one time and installation process was started (I just tried and tried :( ) But i couldn't install at that moment because i was not sure about how to partition my drive. Me Drive Reads the CD i go to the progress bar screen and its stuck .One time even Busy-Box was launched but i am unaware of the commands of Busy-Box .


What really troubles me is the unpredictable behavior of the installer ???

---

### Post by wpshooter on 2008-10-14
Have you checked the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by ^NeoPhyt3^ on 2008-10-14
Yes I have.I have burned 3 different CDs for UBUNTU now and still its not working...... 

Every time i reboot i get to a different step and get stuck there

---

### Post by ^NeoPhyt3^ on 2008-10-14
Guys help me out please ....

What if by CD i use the option Install inside windows and afterwards when my install is done if format windows partition.It wont create any problems right ???

---

### Post by forger on 2008-10-14
a) You get stuck because it shows different errors every time? Then I still recommend trying with another cd/dvd drive.. it doesn't hurt borrowing one :)
b) You get stuck with the installation, meaning you don't know what to do next? Read:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

---

