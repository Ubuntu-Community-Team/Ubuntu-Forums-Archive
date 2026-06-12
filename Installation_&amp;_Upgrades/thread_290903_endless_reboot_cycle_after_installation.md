---
title: "endless reboot cycle after installation"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by freeballer on 2006-11-01
I just tried to install ubuntu server edition 6.1 on an old POS I put together. It was running an old version of debian for some time but needed upgrade so I decided to use ubuntu. Basically a k6 550mhz with 184mb ram (shared with 8mb video) and 20gb HD. I used a disk wiping utility for the hard drive from maxtor and then partitioned / with 5gb /home with 1gb and 2 swap. Installation goes perfect but when it asks to remove cd and reboot I can see the grub menu but it doesn't go past and doesn't give me an error msg just reboots the system. Over and over in an endless cycle](*,)


My first guess was the cd was corrupted but it passed the verification. I also ran a diagnostic on the hard drive which passed with flying colours. I was also thinking about running the live cd installer and see if I can check something there but the cd will not load properly (probably because of the ancient hardware).

Can someone help me out?
Geoff

---

### Post by doobit on 2006-11-01
Well, for starters, can you hit the Esc key and see the Grub menu? 
What's in it?

---

### Post by wpshooter on 2006-11-01
Have you tested the machines memory ?

---

### Post by freeballer on 2006-11-01
I can hit the grub menu and all that's in it is ubuntu 2.6.10-17-server / .... recovery and memtest
neither regular or recovery work.

I have not tested the ram but I assume it's ok since the POS was booted just an hour before to backup my /etc/ /home/ and /var/log from the old debian system. However I will do memtest from the ubuntu menu and see where that takes me. I will post later tonight after jericho and lost if its finished or likely tomorrow the results.

---

### Post by sloggerkhan on 2006-11-01
I had this problem installing xubuntu on a friend's machine. She had 256 megs of RAM and it worked when I turned the video-ram segment taken from system Ram down to 1 or 2 megs instead of 8. Don't know why, but sounds practically identical.

---

### Post by freeballer on 2006-11-02
ram in system tested ok.
changed the default video size from 8mb to 4mb (smallest possible) and same problem... anybody have some other ideas?

---

### Post by garton on 2007-01-14
I have this problem too. Did you find any solution?

---

### Post by freeballer on 2007-01-14
unfortunately no.
I had disconnected and/or tested every physical device I could to try and find a faulty peice of ram, nic, cpu, hd... bios settings, different boot loaders (lilo)... nothing worked!

I hope if someone finds the answer they will post here, i will if I find an answer. But right now I've spent too much time with it. The hard drive is now being used on my main computer

---

### Post by confused57 on 2007-01-14
It's a known bug with the server install cd and certain hardware, in my case it was an AMD K6-2, 500 MHz, and many others with a similar setup have had the same problem.

If you want to install a server, you can use the Alternate install cd.

---

### Post by freeballer on 2007-01-15
can you tell me if it's a bug with certain application (kernel, lilo) as I had similar issues with another distribution I tried afterwards?

---

### Post by az on 2007-01-15
> **confused57 said:**
> It's a known bug with the server install cd and certain hardware, in my case it was an AMD K6-2, 500 MHz, and many others with a similar setup have had the same problem.

If you want to install a server, you can use the Alternate install cd.

It's not a bug, really.  The server kernel is not optimised for anything less than a 686.

An amd-k6 II is not quite a 686-type processor.  You can however boot the install cd again and chroot into your install.  From there, just 

sudo apt-get install linux-image-386 (or linux-image-generic for Edgy)

The installer uses the generic (386) kernel but ends up installing the 686 kernel.

You can also install the kernel from the alternate cd.

---

### Post by confused57 on 2007-01-15
> **azz said:**
> It's not a bug, really.  The server kernel is not optimised for anything less than a 686.

An amd-k6 II is not quite a 686-type processor.  You can however boot the install cd again and chroot into your install.  From there, just 

sudo apt-get install linux-image-386 (or linux-image-generic for Edgy)

The installer uses the generic (386) kernel but ends up installing the 686 kernel.

You can also install the kernel from the alternate cd.

Thanks for clarifying...that makes sense, because I wasn't able to get the Gentoo Live Cd to run on my old machine for that reason, it wouldn't run on less than 686...I ended up having to install Gentoo with the minimal live cd.

---

### Post by creigscofield on 2007-01-15
Can anyone tell me how to install server from the alternate cd?  Do you choose command line install from the main menu or is there an option for server?  I'm trying to setup my k6 500 mhz as a server and don't want it to install any unnecessary components.

---

### Post by az on 2007-01-16
> **creigscofield said:**
> Can anyone tell me how to install server from the alternate cd?  Do you choose command line install from the main menu or is there an option for server?  I'm trying to setup my k6 500 mhz as a server and don't want it to install any unnecessary components.

You can install a server (base system) using the alternate cd.  You then install the lamp packages and you will end up with exactly the same thing as if you had just picked the LAMP installation from the server cd - with the desktop kernel instead of the server kernel.

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

---

### Post by creigscofield on 2007-01-16
I guess I wasn't clear on what I was asking.  When you insert the edgy alternate install cd, a menu comes up that says something to the effect of;
> 
INSTALL FOR OEM
INSTALL IN TEXT MODE
INSTALL A COMMAND LINE SYSTEM
BOOT FROM 1ST HARD DRIVE
CHECK DISK FOR ERRORS

(sorry if this isn't exact, I'm away from the system I was trying to install on right now) My question was since there is no "INSTALL A SERVER" option, do I choose "INSTALL A COMMAND LINE SYSTEM" or does this install any packages that a server install doesn't?  Sorry for the confusion.

---

### Post by confused57 on 2007-01-16
Select the option:
INSTALL A COMMAND LINE SYSTEM

then install the packages azz listed.

---

### Post by creigscofield on 2007-01-16
Thanks

---

### Post by timbo747 on 2008-02-27
Thanks for the info as I have just solved my problem with your help.

The file was removed and the new 386 installed nicely and all boots perfectly now.

Thanks again for posting this fix.

Klaus

---

