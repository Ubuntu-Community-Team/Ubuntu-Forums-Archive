---
title: "Need help installing Ubuntu"
date: 2015-04-11
forum: Installation &amp; Upgrades
---

### Post by GhostlyFox on 2015-04-11
Hi, i currently have Win XP and i want to switch to Ubuntu. I tried installing it with Wubi, UNetBootIn and instlux, also i tried iso image way but none have worked so far.

Using Wubi i get error telling me i dont have enough memory even though i put 30gb installation size.
Using UNetBootIn i dont have option to chose Ubuntu on Choose OS Screen, only have two WINDOWS (default).
Using Instlux it just reboots my computer and then tells me to uninstall... Even if i don't uninstall it and reboot manualy again it wont start installation.

Here is my boot.ini with unetbootin installed

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating system]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP"
C:\ubnldr.mbr="UNetbootin"

Also i cant use Stick and CD way because my computer is very old and bios only has option for floppy disks in removable boot and my comp wont load cds.

The most successful way so far was with Iso Image... I chose Ubuntu and i get gurb command line but idk what to type to initialize installation.

---

### Post by grahammechanical on 2015-04-11
We do not recommend using Wubi.exe as a method to runing Ubuntu. To start with is was only ever meant to be a temporary way of testing Ubuntu. It was not meant for prolonged use. The second and most important reason for not using wubi.exe is that it is no longer under development. It is not supported any more.

With nearly all the methods of installing Ubuntu we need an install medium. Either a DVD disc or an USB memory stick. The installer has to take files off of the DVD disc or USB stick. There is an install method where we have a very small size installer and all the other stuff that makes up a Ubuntu OS is downloaded from the internet. It is called a mini ISO or Network Boot. It is small enough to fit onto a CD with masses of room to spare but not onto a floppy disc. Mini ISO = 30 MB to 40 MB in size.

Besides, If you have a machine that has a BIOS that cannot load from CD drive then the hardware might be too old for Ubuntu and even too old for any of the flavours of Ubuntu. You may need to try with some other Linux distributions.

Tell us the hardware specifications of this machine. CPU? RAM? Video/graphics adapter? That kind of stuff.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

Regards.

---

### Post by GhostlyFox on 2015-04-11
AMD Athlon(tm) Dual Core Processor 4850e
2.51GHz, 1.87 GB of Ram
nVidia GeForce 6150SE nForce 430...
Also my comp is 32Bit

I had Ubuntu few years ago but i installed it via Wubi.. Also i can set boot up to be from cd but not from usb stick.

---

### Post by ajgreeny on 2015-04-11
Your comment > Using Wubi i get error telling me i dont have enough memory even though i put 30gb installation size.has nothing to do with the space you reserved for ubuntu; that is not memory, it is disk space for the installation.  The error was all about RAM, and as your machine was an old XP one without the ability to boot from USB, I suspect it does not have enough RAM to manage a GUI installation.

As grahammechanical says above, wubi is no longer supported so I recommend you forget about that, and if the machine is as old as you seem to be suggesting, you may also need to forget about any of the Ubuntu family of OSs and look at other smaller distros, eg Puppy

EDIT:
I've just seen your specs, which should be fine for the lighter versions such as Xubuntu and Lubuntu, but possibly not Ubuntu itself with the unity desktop which is fairly resource hungry, and needs really good 3D capable graphics.
Do you have a CD or DVD drive?  If it can read DVDs you can install using a live DVD burned from the .iso file, which I assume you already have.

---

### Post by dino99 on 2015-04-11
as you have not much ram, choose lubuntu for example

---

### Post by GhostlyFox on 2015-04-11
Can i install lubuntu using UNetBootin ?

---

### Post by GhostlyFox on 2015-04-11
Just saw your edit.. And yes i have CD Drive but the problem is that one CD Drive is plug off cause cable for some reason there aren't two cables and i tried to remove cable from the CD Drive that isn't working but it wont come off... Thats why i am trying to use installers, but no luck with them...

---

### Post by GhostlyFox on 2015-04-11
[FONT=arial]This is what boot.ini has after UNetBootIn

[/FONT]C:\ubnldr.mbr="UNetbootin"

but it won't load it after reboot.. 
It say's Failed to load boot.ini
Booting from c:\WINDOWS

---

### Post by mörgæs on 2015-04-11
While you still have Windows you could consider upgrading the BIOS. Might solve the booting problem.

---

