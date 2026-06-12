---
title: "xubuntu amd64 10.04 plymouth and nomodeset"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by isosi on 2010-02-18
I like system when it is small, fast and modular and of course hardware compatible as far as needed for normal desktop use. So ubuntu is for me. If it will be possible too fit install in 200mb so it will be perfect system. Actually i don't understand why xubuntu 10.04 use 2gb on my hdd?
If i understand that, then may be it will not be such question. 

But lets back to title ;)

1 - problem and temporary solution. 

After install i have to remove plymouth (0.80)to get rid of PC lock up whenever when once pressed Enter. It is no problem if using only mouse ;)
But i have restarted PC may be 5 times, until removed plymouth with synaptic #-o, because in some step i was by habit pressing not OK with mouse but Enter on keyboard. It was nice game to find out how much i am used to use Enter.

2 - problem and temporary solution.

I use old CRT monitor Hitachi cm772, and it was started with resolution 
1600x1200 85hz (so it was written in program "Display" panel, about correctness of 85hz it is really big "???"). Usually i use this monitor in mode of 1024x786 85hz, because else way (like 1600x1200) i get my eyes batteries flat very quickly on working like microscope mode. So it is natural in this situation that i would like to go to eye battery saving mode that is 1024x786 85hz (or more hz like 100hz). 
In menu (it is Xubuntu) Applications > Settings > Display i found that 1024x786 and forced 85hz (it was not possible to choose another refresh rate). So i choose this configuration and get black screen and in few seconds monitor was showing nice green title "Safe mode" and in few more seconds just black screen. 

The solution is during boot keep Shift key to get Grub2 menu, then choose wanted kernel line and pres "e" (edit) on keyboard. Then in new menu in kernel line (some where close to the end) ad text nomodeset and press Ctrl+x (to boot using this configuration).  

After that i began to use Xubuntu 10.04 like normal and usual desktop system.

p.s.

But there is still one little question that takes 2gb of my hdd:

Actually i don't understand why xubuntu 10.04 use 2gb on my hdd?

*******

technical data of pc:

uname -na

Linux username 2.6.32-13-generic #18-Ubuntu SMP Wed Feb 10 21:32:38 UTC 2010 x86_64 GNU/Linux

lspci

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)

---

### Post by isosi on 2010-02-18
just few minutes ago i find out that sound (Realtec ALC1200 oss mixer)
was making no sound :popcorn:
Then i find out missing update stuff (scary 120mb). After update sound is working.

---

### Post by bobcollard on 2010-02-20
What measurement are you using to find out how much room is taken on your HD?  You do know there is empty space for the swap file and the formating takes up some space.  I'm using Xubuntu 9.10, just curious.

---

### Post by isosi on 2010-02-22
I am talking about this ;)

df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda2  4.6G 2.3G  2.1G  53% /

I would like to have in "Used" less than 1G, because it is 21 century :D
Logical thinking, code should not only get bigger.
The code should get more smart, and more likely when code get smarter it become smaller.

That is simple logic :popcorn:

---

### Post by bobcollard on 2010-02-22
> **isosi said:**
> I am talking about this ;)

df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda2  4.6G 2.3G  2.1G  53% /

I would like to have in "Used" less than 1G, because it is 21 century :D
Logical thinking, code should not only get bigger.
The code should get more smart, and more likely when code get smarter it become smaller.

That is simple logic :popcorn:
bob@dell-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             141G   11G  123G   8% /
What does this tell you?  It's like this, my computer has a 160GB HD and the system, the only one on the HD, takes up what it wants, not what it needs.  There is a minimum amount it can take, if you had set up a partition giving it only that amount, that's what it would take.
One last question, how many KB are your Pictures, Music and other personal items taking up?  I have 8GB of music in there somewhere.

---

### Post by isosi on 2010-02-23
sda2 is only system. The personal data is in separate partition, like and boot data. But my wonder is about the system size on hdd and has nothing to do with some technical or programing setup it is just wonder, how things are going in general by time.



I remember a time when ubuntu 4.10 xfce install used less than 1G (just only system, no personal data). But of course i understand that this is not connected with one line in some config file, it is  all system :popcorn: 
Simply even kernel now is bigger than in ubuntu 4.10 time, and system has much better hardware support now and of course system now  has new stuff inside.

---

### Post by bobcollard on 2010-02-23
> **isosi said:**
> sda2 is only system. The personal data is in separate partition, like and boot data. But my wonder is about the system size on hdd and has nothing to do with some technical or programing setup it is just wonder, how things are going in general by time.



I remember a time when ubuntu 4.10 xfce install used less than 1G (just only system, no personal data). But of course i understand that this is not connected with one line in some config file, it is  all system :popcorn: 
Simply even kernel now is bigger than in ubuntu 4.10 time, and system has much better hardware support now and of course system now  has new stuff inside.
bob@dell-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             141G   11G  123G   9% /
udev                  1.5G  308K  1.5G   1% /dev
none                  1.5G     0  1.5G   0% /dev/shm
none                  1.5G   84K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
This is my complete readout for that command, notice: no SDA2?  So, where is my system compared with the rest of it?  If it is udev, then it's only using 308K of 1.5GB.  I'm not trying to argue, just to point out your figures are incorrect.
Xubuntu installer states: "To install Xubuntu, you need 2.0 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk."  That's to install because they unpack and install things there then at the end you see some applets removed.  The actual space used is less.

---

### Post by isosi on 2010-02-27
As i sea  your system is installed in the first partition (sda1) and declare using 11G ;) 
Mine is in the second partition thats why it is sda2.

When i was talking about amount of memory system is using, a have in mind 
hdd space taken by files, pipes, file system and so on, but not some temporary files. :popcorn:

---

