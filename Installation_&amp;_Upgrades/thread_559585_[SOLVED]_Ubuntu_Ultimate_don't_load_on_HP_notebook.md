---
title: "[SOLVED] Ubuntu Ultimate don't load on HP notebook"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by Newbie1978 on 2007-09-25
I recently purchase a new HP notebook and I honestly thought that this will be better than my no so old Acer turion 64 TK-53  2.0 GHZ at least on hardware my HP looks superior, but much to my surprise the ACER work faster, better, and with more stability than my new "hardware superior" HP, I'm not sure why but the only explanation is that the terrible Windows vista home factory install form HP is messing up everything, while in rest with absolutely no programs running not even the messenger Vista have almost 70 process running that takes about 65% of the physical memory (more than 600 MB) just for the background programs and services, Vista freezes  all the time while burning a DVD which is bad, or just web browsing which is even worst, the Acer works great with XP with very little problems from time to time but nothing that a good tune up can't fix.

After trying Linux Ubuntu Ultimate at work I found that this is not a very friendly OS mostly when I try to make it work with some application that I use daily or when installing new drivers or some programs that just don't work, but Ubuntu give me the stability that Vista can't offer and I'm more then willing to learn how to deal with Linux just to show Microsoft the finger and move on to a different OS.

Now the DVD that I use at work for my desktop does not work on my notebook I follow an advice that I read i another forum and burned a copy of the ISO at 4X speed and I got the same problem, when loading I get this on a black screen

PIDOF [3266] can't read sid from proc /1/stat
PIDOF [3266] can't read sid from proc /10/stat
PIDOF [3266] can't read sid from proc /11/stat
PIDOF [3266] can't read sid from proc /163/stat

After a while eventually load some parts of the OS but in the end it freezes on a black screen and does nothing so I have to hard reset the machine in order to at least have Vista working.

My specs are:

Processor AMD Athlon 64 X2 TK-53  1.7 GHZ
HARD DRIVE 120 GB Serial ATA hard drive
1 GB RAM (2 GB max), 
MASHITA 8x DVD-/+RW drive ATA device
Connectivity: 3 USB, 1 FireWire, 1 VGA, 1 S-Video, expansion port 3 connector, ExpressCard 54/34, 5-in-1 memory card reader
54g Wi-Fi LAN (802.11b/g), 10/100 Ethernet
Nvidia GeForce Go 6150 video card with up to 287 MB shared memory
Pre-installed with Windows Vista Home Premium 32 BIT OS

Please help I really would like to try Linux on my notebook

---

### Post by ddrichardson on 2007-09-25
I have a couple of HP laptops, they all play with Ubuntu fine but only if you specify the noapic option on boot. Choose F6 from the menu and add noapic to the end of the kernel line.

---

### Post by Newbie1978 on 2007-09-27
> **ddrichardson said:**
> I have a couple of HP laptops, they all play with Ubuntu fine but only if you specify the noapic option on boot. Choose F6 from the menu and add noapic to the end of the kernel line.

Great advice men works like a charmed after the OS load I install it and works great, GOOD BYE VISTA!!!!!!!!!!!! HELLO LINUX UBUNTU ULTIMATE

---

### Post by ddrichardson on 2007-09-27
Welcome to Ubuntu, can you mark the thread solved to assist others searching for the same problem, there's a link in my sig.

---

